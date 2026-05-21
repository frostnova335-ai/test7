import { useState, useRef, useCallback } from "react";

// ─── Types ────────────────────────────────────────────────────────────────────

type View = "search" | "dashboard" | "saved" | "alerts";
type SearchType = "semantic" | "pattern" | "similar" | "anomaly";
type DetailTab = "transcript" | "analysis" | "moments";
type Sentiment = "negative" | "positive" | "neutral";
type InsightChipClass = "red" | "blue" | "green";

interface TranscriptLine {
    speaker: "AGENT" | "CUST";
    text: string;
    time: string;
    emotion: string;
}

interface Moment {
    time: string;
    text: string;
    type: string;
}

interface Analysis {
    summary: string;
    scores: Record<string, number>;
    moments: Moment[];
}

interface CallStats {
    duration: string;
    hold: string;
    transfers: number;
    score: number;
}

interface Call {
    id: string;
    agent: string;
    date: string;
    duration: string;
    queue: string;
    sentiment: Sentiment;
    snippet: string;
    tags: string[];
    stats: CallStats;
    transcript: TranscriptLine[];
    analysis: Analysis;
}

interface InsightChip {
    label: string;
    cls: InsightChipClass;
}

interface SummaryData {
    text: string;
    chips: InsightChip[];
}

// ─── Static Data ──────────────────────────────────────────────────────────────

const AVATARS = ["#e8d0cc", "#ccd4e8", "#cce8d4", "#e8e4cc", "#d4cce8"];
const COLORS = ["#c0543a", "#3a6bc0", "#3a9c5e", "#9c893a", "#7a3a9c"];

const CALLS: Call[] = [
    {
        id: "CC-2024-084721",
        agent: "Marcus T.",
        date: "Today, 09:14",
        duration: "8m 42s",
        queue: "Billing",
        sentiment: "negative",
        snippet:
            'Customer opened with "I\'ve been charged twice this month and I want an explanation now." Agent attempted to look up account but struggled with system slowness. Customer became increasingly frustrated saying they\'d been loyal for 6 years and this was unacceptable. Agent offered £10 credit but customer rejected it...',
        tags: ["billing", "churn", "repeat-contact"],
        stats: { duration: "8m 42s", hold: "2m 10s", transfers: 1, score: 2.1 },
        transcript: [
            { speaker: "CUST", text: "Hi, I've been charged twice this month and I need someone to explain this right now.", time: "00:04", emotion: "😤 Frustrated" },
            { speaker: "AGENT", text: "I completely understand your concern. Let me pull up your account right away. Can I take your account number or postcode to verify?", time: "00:12", emotion: "😐 Neutral" },
            { speaker: "CUST", text: "It's PO12 4AB. And I've been a customer for six years — six years — and this is the treatment I get.", time: "00:24", emotion: "😠 Angry" },
            { speaker: "AGENT", text: "I can see your account… there does appear to be a duplicate transaction from the 3rd. I'm so sorry about that. Let me see what I can do here.", time: "01:05", emotion: "😟 Apologetic" },
            { speaker: "CUST", text: "So can you just tell me — is it going to be refunded? I shouldn't have to fight for this.", time: "01:28", emotion: "😤 Frustrated" },
            { speaker: "AGENT", text: "Absolutely. I'm going to raise a refund now for the £42.99. It should be back within 3 to 5 working days.", time: "01:41", emotion: "😌 Reassuring" },
            { speaker: "CUST", text: "Three to five days? I'm living month to month and that's my money. Can't you do it faster?", time: "01:55", emotion: "😠 Distressed" },
        ],
        analysis: {
            summary: "Call involved a billing double-charge that was legitimate. Agent handled the factual resolution correctly but was slow to empathise initially, which caused sentiment to deteriorate further before recovery. Churn risk rated HIGH based on customer language.",
            scores: { empathy: 55, firstCallRes: 80, compliance: 90, pace: 45 },
            moments: [
                { time: "00:04", text: "Customer opened with clear frustration signal — double charge complaint.", type: "⚡ Trigger Event" },
                { time: "01:05", text: "Agent confirmed issue — this was the critical de-escalation window.", type: "🎯 Key Moment" },
                { time: "01:55", text: "Customer expressed financial distress — churn language detected.", type: "⚠️ Churn Signal" },
                { time: "03:12", text: "Agent did not offer expedited refund option — opportunity missed.", type: "❌ Coaching Point" },
            ],
        },
    },
    {
        id: "CC-2024-084618",
        agent: "Priya K.",
        date: "Today, 08:52",
        duration: "12m 14s",
        queue: "Retentions",
        sentiment: "negative",
        snippet:
            "Customer called to cancel their subscription explicitly saying they found a competitor offering the same service at 40% less. Agent Priya handled the call well — probing the competitor details before presenting a personalised retention offer. Customer was close to accepting but ultimately declined saying they needed to think...",
        tags: ["cancellation", "churn", "competitor-mention"],
        stats: { duration: "12m 14s", hold: "0m 42s", transfers: 0, score: 3.8 },
        transcript: [
            { speaker: "CUST", text: "I'd like to cancel my subscription please. I've found a better deal elsewhere.", time: "00:06", emotion: "😐 Decided" },
            { speaker: "AGENT", text: "I'm sorry to hear that. Before I process anything, would you mind sharing what you've found? I want to make sure we can't match it for you.", time: "00:14", emotion: "💬 Probing" },
            { speaker: "CUST", text: "SwitchEasy. They're doing the same plan for £24.99 a month. We pay £42. That's a big difference.", time: "00:28", emotion: "😐 Factual" },
            { speaker: "AGENT", text: "I appreciate you telling me. So just to understand — is it purely price, or is there something about your experience with us that's also been a factor?", time: "00:40", emotion: "🎯 Skilled" },
            { speaker: "CUST", text: "Honestly? Mainly price. We've not had a bad experience per se. Just… it's a lot of money.", time: "00:58", emotion: "😔 Soft" },
            { speaker: "AGENT", text: "That's really helpful. Given you've been with us 3 years and this is purely about price, I can actually offer you our loyalty rate — that would bring you down to £26.99 with all the same features.", time: "01:15", emotion: "💡 Offer" },
        ],
        analysis: {
            summary: "High-quality retention call. Agent correctly identified that this was price-only churn, not experience-driven. Personalised retention offer was appropriate. Lost on a small price gap — follow-up recommended at 7 days.",
            scores: { empathy: 88, firstCallRes: 70, compliance: 95, pace: 82 },
            moments: [
                { time: "00:28", text: "Competitor \"SwitchEasy\" named — first contact with emerging trend.", type: "📊 Competitor Signal" },
                { time: "00:40", text: "Agent's diagnostic question was textbook — uncovered price-only motive.", type: "⭐ Best Practice" },
                { time: "01:15", text: "Loyalty rate offer was appropriate and well-timed.", type: "🎯 Retention Moment" },
            ],
        },
    },
    {
        id: "CC-2024-084502",
        agent: "James O.",
        date: "Today, 08:31",
        duration: "3m 07s",
        queue: "Billing",
        sentiment: "negative",
        snippet:
            "Very short call — customer called about unexpected charge and agent did not properly verify account before disclosing the last 4 digits of their card on file. This is a compliance breach — the account verification step was skipped entirely. Customer did not appear fraudulent but the protocol failure is flagged...",
        tags: ["compliance", "security", "coaching"],
        stats: { duration: "3m 07s", hold: "0m 0s", transfers: 0, score: 1.2 },
        transcript: [
            { speaker: "CUST", text: "Hi yes, I just got a charge for £19.99 and I don't know what it is.", time: "00:06", emotion: "😐 Confused" },
            { speaker: "AGENT", text: "Sure, let me look that up. Can I take your name?", time: "00:11", emotion: "😐 Neutral" },
            { speaker: "CUST", text: "Jane Williams.", time: "00:14", emotion: "😐 Neutral" },
            { speaker: "AGENT", text: "Okay Jane, I can see that charge — it's for your annual plan renewal. The card ending 4821 was charged on the 2nd.", time: "00:22", emotion: "😐 Neutral" },
            { speaker: "CUST", text: "Oh okay, that makes sense. Thanks.", time: "00:31", emotion: "😊 Resolved" },
        ],
        analysis: {
            summary: "CRITICAL COMPLIANCE FAILURE: Agent disclosed card details (last 4 digits) without completing the mandatory 3-point account verification. Call resolved factually but represents a security protocol breach requiring immediate coaching.",
            scores: { empathy: 60, firstCallRes: 100, compliance: 5, pace: 90 },
            moments: [
                { time: "00:11", text: "Verification started — only name collected, no postcode, DOB, or account PIN.", type: "⚠️ Protocol Breach" },
                { time: "00:22", text: "COMPLIANCE FAIL — card data disclosed before completing verification.", type: "🚨 Critical Flag" },
            ],
        },
    },
    {
        id: "CC-2024-084390",
        agent: "Lisa C.",
        date: "Today, 08:19",
        duration: "6m 53s",
        queue: "Technical Support",
        sentiment: "neutral",
        snippet:
            "Customer had a recurring broadband dropout issue — this was their third call in 5 days on the same problem. Previous tickets had been closed without confirmation of resolution. Lisa correctly identified the repeat pattern and escalated to a specialist team rather than applying the same fix again...",
        tags: ["repeat-contact", "technical", "escalation"],
        stats: { duration: "6m 53s", hold: "1m 20s", transfers: 1, score: 4.2 },
        transcript: [
            { speaker: "CUST", text: "Hi. My broadband is dropping out again. I've called about this twice already this week.", time: "00:06", emotion: "😤 Tired" },
            { speaker: "AGENT", text: "I'm really sorry to hear that — let me pull up your case notes. I can see the two previous calls… and I can see both times an engineer reset your line remotely. Has it helped at all?", time: "00:18", emotion: "🎯 Empathetic" },
            { speaker: "CUST", text: "No. It's fine for a day then drops again every evening around 7pm.", time: "00:32", emotion: "😔 Resigned" },
            { speaker: "AGENT", text: "That time pattern is actually really useful information — evening drops like that often point to a line capacity issue rather than your equipment. I'm not going to do the same reset again. I'm going to escalate this to our network specialist team who can check the exchange level.", time: "00:48", emotion: "💡 Diagnostic" },
        ],
        analysis: {
            summary: "Good call handling of a repeat contact scenario. Agent correctly avoided repeating the failed fix and used the customer's time-specific pattern to identify a likely network-level issue. Escalation was appropriate.",
            scores: { empathy: 84, firstCallRes: 65, compliance: 100, pace: 78 },
            moments: [
                { time: "00:06", text: "Third call — repeat contact detected in case history.", type: "🔁 Repeat Pattern" },
                { time: "00:48", text: "Agent correctly diagnosed time-pattern and escalated — best practice.", type: "⭐ Best Practice" },
            ],
        },
    },
];

const SUMMARIES: Record<string, SummaryData> = {
    billing: {
        text: "247 calls found. The dominant theme is a <strong>billing double-charge incident</strong> concentrated today between 06:00–09:30, affecting 89 unique customers. Secondary cluster: customers questioning annual renewal charges. Average handle time in this set is 9m 14s — 34% above queue baseline. Churn language detected in 31% of matched calls.",
        chips: [
            { label: "89 double-charge calls", cls: "red" },
            { label: "Churn risk: 31%", cls: "red" },
            { label: "AHT +34%", cls: "blue" },
            { label: "FCR: 61%", cls: "green" },
        ],
    },
    competitor: {
        text: '41 calls found mentioning a competitor. <strong>"SwitchEasy"</strong> appears in 47% of matches — a new entrant not previously tracked. Customers referencing competitor are 2.3× more likely to cancel within 14 days. Price is the primary driver (cited in 89% of calls). Only 34% received a retention offer.',
        chips: [
            { label: "SwitchEasy ×47 today", cls: "red" },
            { label: "2.3× churn likelihood", cls: "red" },
            { label: "Only 34% offered retention", cls: "blue" },
        ],
    },
    default: {
        text: "Found <strong>247 matching calls</strong> using semantic analysis. Results are ranked by relevance and recency. Negative sentiment detected in 61% of matched calls — significantly above the 23% baseline. Top themes: billing errors, account access issues, and cancellation intent.",
        chips: [
            { label: "61% negative sentiment", cls: "red" },
            { label: "23% baseline", cls: "blue" },
            { label: "247 results", cls: "green" },
        ],
    },
};

// ─── Helper functions ─────────────────────────────────────────────────────────

function getSummaryKey(q: string): string {
    const lower = q.toLowerCase();
    if (lower.includes("billing") || lower.includes("charge")) return "billing";
    if (lower.includes("competitor") || lower.includes("mention")) return "competitor";
    return "default";
}

function getTagClass(tag: string): string {
    if (tag === "compliance") return "tag compliance";
    if (tag === "churn" || tag === "cancellation") return "tag churn";
    if (tag === "escalation") return "tag escalation";
    return "tag";
}

function getSentimentClass(s: Sentiment): string {
    return s === "negative" ? "sent-negative" : s === "positive" ? "sent-positive" : "sent-neutral";
}

function getSentimentLabel(s: Sentiment): string {
    return s === "negative" ? "😤 Negative" : s === "positive" ? "😊 Positive" : "😐 Neutral";
}

function getScoreColor(v: number): string {
    return v > 75 ? "var(--success)" : v > 50 ? "var(--warn)" : "var(--accent)";
}

function getStatScoreColor(score: number): string {
    return score < 3 ? "var(--accent)" : score > 4 ? "var(--success)" : "var(--warn)";
}

function formatScoreLabel(key: string): string {
    return key.replace(/([A-Z])/g, " $1").replace(/^./, (s) => s.toUpperCase());
}

// ─── Sub-components ───────────────────────────────────────────────────────────

interface InsightChipProps { label: string; cls: InsightChipClass }
function InsightChipBadge({ label, cls }: InsightChipProps) {
    return <span className={`insight-chip ${cls}`}>{label}</span>;
}

interface AISummaryCardProps { text: string; chips: InsightChip[] }
function AISummaryCard({ text, chips }: AISummaryCardProps) {
    return (
        <div className="ai-summary">
            <div className="ai-summary-header">
                <span className="ai-tag">✦ AI Summary</span>
            </div>
            <div className="ai-summary-body" dangerouslySetInnerHTML={{ __html: text }} />
            <div className="ai-insight-chips">
                {chips.map((c, i) => <InsightChipBadge key={i} label={c.label} cls={c.cls} />)}
            </div>
        </div>
    );
}

interface CallCardProps {
    call: Call;
    index: number;
    isSelected: boolean;
    onSelect: (call: Call) => void;
}
function CallCard({ call, index, isSelected, onSelect }: CallCardProps) {
    const aIdx = index % AVATARS.length;
    const initials = call.agent.split(" ").map((w) => w[0]).join("");

    return (
        <div
            className={`call-card${isSelected ? " selected" : ""}`}
            style={{ animationDelay: `${index * 0.05}s` }}
            onClick={() => onSelect(call)}
        >
            <div className="card-top">
                <div
                    className="agent-avatar"
                    style={{ background: AVATARS[aIdx], color: COLORS[aIdx] }}
                >
                    {initials}
                </div>
                <div className="card-meta">
                    <div className="card-id">{call.id}</div>
                    <div className="card-agent">
                        {call.agent}{" "}
                        <span style={{ fontWeight: 400, color: "var(--muted)" }}>— {call.queue}</span>
                    </div>
                    <div className="card-date">{call.date}</div>
                </div>
                <span className={`sentiment-badge ${getSentimentClass(call.sentiment)}`}>
                    {getSentimentLabel(call.sentiment)}
                </span>
            </div>

            <div className="card-snippet">{call.snippet}</div>

            <div className="card-tags">
                {call.tags.map((t) => (
                    <span key={t} className={getTagClass(t)}>{t}</span>
                ))}
            </div>

            <div className="card-stats">
                <span className="card-stat">⏱ <strong>{call.stats.duration}</strong></span>
                <span className="card-stat">⏸ <strong>{call.stats.hold}</strong> hold</span>
                <span className="card-stat">↔ <strong>{call.stats.transfers}</strong> transfers</span>
                <span className="card-stat" style={{ color: getStatScoreColor(call.stats.score) }}>
                    ★ <strong>{call.stats.score}</strong>
                </span>
            </div>
        </div>
    );
}

interface TranscriptViewProps { call: Call }
function TranscriptView({ call }: TranscriptViewProps) {
    const extraTurns = Math.floor(Math.random() * 20) + 5;
    return (
        <>
            {call.transcript.map((line, i) => {
                const isAgent = line.speaker === "AGENT";
                return (
                    <div key={i} className="transcript-line" style={{ animationDelay: `${i * 0.05}s` }}>
                        <div className={`line-speaker ${isAgent ? "speaker-agent" : "speaker-cust"}`}>
                            {line.speaker}
                        </div>
                        <div>
                            <div className={`line-bubble ${isAgent ? "agent" : "cust"}`}>{line.text}</div>
                            <div style={{ display: "flex", gap: 12 }}>
                                <div className="line-time">{line.time}</div>
                                <div className="emotion-indicator">{line.emotion}</div>
                            </div>
                        </div>
                    </div>
                );
            })}
            {call.transcript.length > 0 && (
                <div style={{ textAlign: "center", padding: 16, fontSize: 11, color: "var(--muted)" }}>
                    + {extraTurns} more turns in this conversation
                </div>
            )}
        </>
    );
}

interface AnalysisViewProps { call: Call }
function AnalysisView({ call }: AnalysisViewProps) {
    const { summary, scores } = call.analysis;
    return (
        <>
            <div className="analysis-block">
                <div className="analysis-title">✦ AI Summary</div>
                <div className="analysis-text">{summary}</div>
            </div>
            <div className="analysis-block">
                <div className="analysis-title">Quality Scores</div>
                {Object.entries(scores).map(([k, v]) => (
                    <div key={k} className="score-bar">
                        <div className="score-label">
                            <span>{formatScoreLabel(k)}</span>
                            <span>{v}/100</span>
                        </div>
                        <div className="score-track">
                            <div className="score-fill" style={{ width: `${v}%`, background: getScoreColor(v) }} />
                        </div>
                    </div>
                ))}
            </div>
        </>
    );
}

interface MomentsViewProps { call: Call }
function MomentsView({ call }: MomentsViewProps) {
    return (
        <div className="analysis-block">
            <div className="analysis-title">Key Moments &amp; Coaching Points</div>
            {call.analysis.moments.map((m, i) => (
                <div key={i} className="moment-item">
                    <div className="moment-time">{m.time}</div>
                    <div>
                        <div className="moment-text">{m.text}</div>
                        <div className="moment-type">{m.type}</div>
                    </div>
                </div>
            ))}
        </div>
    );
}

interface DetailPanelProps {
    selectedCall: Call | null;
    activeTab: DetailTab;
    onTabChange: (tab: DetailTab) => void;
}
function DetailPanel({ selectedCall, activeTab, onTabChange }: DetailPanelProps) {
    if (!selectedCall) {
        return (
            <div className="detail-panel">
                <div className="empty-state" style={{ display: "flex" }}>
                    <div className="empty-icon">👆</div>
                    <div className="empty-title">Select a call</div>
                    <div className="empty-text">
                        Click any result on the left to read its full transcript and AI analysis.
                    </div>
                </div>
            </div>
        );
    }

    const sentClass =
        selectedCall.sentiment === "negative"
            ? "sent-negative"
            : selectedCall.sentiment === "positive"
                ? "sent-positive"
                : "sent-neutral";

    return (
        <div className="detail-panel" style={{ display: "flex", flexDirection: "column", height: "100%" }}>
            <div className="detail-header">
                <div className="detail-call-id">{selectedCall.id}</div>
                <div className="detail-title">{selectedCall.agent} · {selectedCall.queue}</div>
                <div className="detail-meta-row">
                    <span className="detail-meta-item">📅 {selectedCall.date}</span>
                    <span className="detail-meta-item">⏱ {selectedCall.duration}</span>
                    <span className="detail-meta-item">📂 {selectedCall.queue}</span>
                    <span className={`detail-meta-item sentiment-badge ${sentClass}`}>
                        {selectedCall.sentiment}
                    </span>
                </div>
            </div>

            <div className="detail-tabs">
                {(["transcript", "analysis", "moments"] as DetailTab[]).map((tab) => (
                    <div
                        key={tab}
                        className={`detail-tab${activeTab === tab ? " active" : ""}`}
                        onClick={() => onTabChange(tab)}
                    >
                        {tab.charAt(0).toUpperCase() + tab.slice(1)}
                    </div>
                ))}
            </div>

            <div className="detail-body" style={{ flex: 1, overflowY: "auto" }}>
                {activeTab === "transcript" && <TranscriptView call={selectedCall} />}
                {activeTab === "analysis" && <AnalysisView call={selectedCall} />}
                {activeTab === "moments" && <MomentsView call={selectedCall} />}
            </div>
        </div>
    );
}

// ─── View: Search ─────────────────────────────────────────────────────────────

interface SearchViewProps {
    searchQuery: string;
    setSearchQuery: (q: string) => void;
    searchType: SearchType;
    setSearchType: (t: SearchType) => void;
    hasResults: boolean;
    summary: SummaryData | null;
    selectedCall: Call | null;
    activeTab: DetailTab;
    onSearch: () => void;
    onUseQuery: (q: string) => void;
    onSelectCall: (call: Call) => void;
    onTabChange: (tab: DetailTab) => void;
}

function SearchView({
    searchQuery, setSearchQuery, searchType, setSearchType,
    hasResults, summary, selectedCall, activeTab,
    onSearch, onUseQuery, onSelectCall, onTabChange,
}: SearchViewProps) {
    const suggestions = [
        "calls where customer mentioned competitor",
        "repeat caller within 7 days on same issue",
        "calls where customer mention process issues",
        "calls where CSAT is less then 3",
        "calls where CES is high",
        "calls where emotion is frustrated",
        "calls where follow up is promised",
        "calls where FCR achieved",
    ];

    const searchTypes: { key: SearchType; label: string }[] = [
        { key: "semantic", label: "🧠 Semantic" },
        { key: "pattern", label: "🔗 Pattern / Sequence" },
        { key: "similar", label: "🎯 Find Similar" },
        { key: "anomaly", label: "⚡ Anomaly" },
    ];

    return (
        <div className="view active" style={{ flexDirection: "column", height: "100%" }}>
            {/* Search Hero */}
            <div className="search-hero">
                <div className="search-title">Find any conversation.</div>
                <div className="search-sub">
                    Semantic search across 2.4 million call transcripts — try anything in plain language.
                </div>
                <div className="search-box-wrap">
                    <input
                        id="mainSearchInput"
                        className="main-search"
                        type="text"
                        placeholder="e.g. Customer angry about billing and asked to cancel subscription…"
                        value={searchQuery}
                        onChange={(e) => setSearchQuery(e.target.value)}
                        onKeyUp={(e) => {
                            if (e.key === "Enter") {
                                handleSearch();
                            }
                        }}
                    />
                    {/* <button className="search-btn" onClick={onSearch}>
                        🔍
                    </button> */}

                    <button
                        className="search-btn"
                        onClick={onSearch}
                        disabled={loading}
                    >
                        {loading ? "Searching..." : "SEARCH"}
                    </button>
                </div>
                {/* <div className="search-type-row">
          {searchTypes.map(({ key, label }) => (
            <span
              key={key}
              className={`type-pill${searchType === key ? " active" : ""}`}
              onClick={() => setSearchType(key)}
            >
              {label}
            </span>
          ))}
        </div> */}
            </div>

            {/* Suggestions */}
            <div className="suggestion-row">
                <span
                    style={{
                        fontSize: 11,
                        color: "var(--muted)",
                        marginRight: 8,
                        whiteSpace: "nowrap",
                        paddingTop: 8,
                        fontWeight: 600,
                    }}
                >
                    Try:
                </span>

                <div className="suggestion-scroll">
                    {suggestions.map((s) => (
                        <div
                            key={s}
                            className="suggest-chip"
                            onClick={() => onUseQuery(s)}
                        >
                            {s}
                        </div>
                    ))}
                </div>
            </div>

            {/* Pattern Builder */}
            {searchType === "pattern" && (
                <div style={{ padding: "20px 36px" }}>
                    <div className="pattern-builder">
                        <div className="pattern-header">
                            <span className="ai-tag">PATTERN SEARCH — build a call sequence</span>
                        </div>
                        <div className="pattern-steps">
                            <div className="pattern-step"><span className="step-num">1</span> Agent offered retention discount</div>
                            <div className="pattern-arrow">→</div>
                            <div className="pattern-step"><span className="step-num">2</span> Customer acknowledged offer</div>
                            <div className="pattern-arrow">→</div>
                            <div className="pattern-step"><span className="step-num">3</span> Call ended with churn</div>
                            <div className="pattern-arrow">→</div>
                            <div className="pattern-step" style={{ borderStyle: "dashed", color: "rgba(255,255,255,0.3)" }}>
                                + Add step
                            </div>
                        </div>
                    </div>
                    <div style={{ fontSize: 12, color: "var(--muted)", marginBottom: 16 }}>
                        Match calls where all steps occur in sequence. Found{" "}
                        <strong style={{ color: "var(--ink)" }}>1,247 calls</strong> matching this pattern from last 90 days.
                    </div>
                </div>
            )}

            {/* Filter Bar */}
            {hasResults && (
                <div className="filter-bar">
                    <span className="filter-label">Refine:</span>
                    {[
                        { opts: ["All Dates", "Today", "Last 7 Days", "Last 30 Days", "Custom Range"] },
                        { opts: ["All Queues", "Billing", "Technical Support", "Retentions", "New Sales"] },
                        { opts: ["All Sentiment", "Negative", "Neutral", "Positive"] },
                        { opts: ["All Outcomes", "Resolved", "Escalated", "Transferred", "Callback Needed"] },
                    ].map((sel, i) => (
                        <select key={i} className="filter-select">
                            {sel.opts.map((o) => <option key={o}>{o}</option>)}
                        </select>
                    ))}
                    <span className="result-count">
                        Showing <strong>247 results</strong> for your query
                    </span>
                </div>
            )}

            {/* Results Area */}
            {hasResults && summary && (
                <div className="results-area" style={{ display: "grid", flex: 1, overflow: "hidden" }}>
                    {/* Left: Results List */}
                    <div className="results-list">
                        <AISummaryCard text={summary.text} chips={summary.chips} />
                        <div>
                            {CALLS.map((call, i) => (
                                <CallCard
                                    key={call.id}
                                    call={call}
                                    index={i}
                                    isSelected={selectedCall?.id === call.id}
                                    onSelect={onSelectCall}
                                />
                            ))}
                        </div>
                    </div>

                    {/* Right: Detail Panel */}
                    <DetailPanel
                        selectedCall={selectedCall}
                        activeTab={activeTab}
                        onTabChange={onTabChange}
                    />
                </div>
            )}
        </div>
    );
}

// ─── View: Dashboard ──────────────────────────────────────────────────────────

function DashboardView() {
    const kpis = [
        { icon: "📞", val: "1,847", label: "Calls Today", delta: "↑ 12% vs yesterday", dir: "up", valColor: undefined },
        { icon: "😤", val: "23%", label: "Negative Sentiment", delta: "↑ 4pp — billing spike", dir: "down", valColor: "var(--accent)" },
        { icon: "✅", val: "68%", label: "First Call Resolution", delta: "↓ 2pp — watch", dir: "down", valColor: "var(--success)" },
        { icon: "⚠️", val: "41", label: "Compliance Flags", delta: "↑ 8 since yesterday", dir: "down", valColor: "var(--warn)" },
    ];

    const trends = [
        { label: "Billing Dispute", pct: 78, color: "var(--accent)" },
        { label: "Technical Fault", pct: 54, color: "var(--accent2)" },
        { label: "Account Access", pct: 41, color: "var(--gold)" },
        { label: "Cancellation", pct: 32, color: "#8a38b2" },
        { label: "Shipping Delay", pct: 22, color: "var(--success)" },
    ];

    const alerts = [
        { color: "var(--accent)", text: "Billing complaint volume up 34% in last 2 hours — possible system error", meta: "Triggered 14 min ago · 127 matching calls" },
        { color: "var(--warn)", text: "Agent Sarah M. — 4 escalations in last 30 min, coaching flag raised", meta: "Triggered 28 min ago · Retentions queue" },
        { color: "#8a38b2", text: "New competitor mention trend: \"SwitchEasy\" mentioned 47× today (baseline: 3×)", meta: "Triggered 1 hr ago · Emerging signal" },
    ];

    return (
        <div className="view active" style={{ flexDirection: "column" }}>
            <div className="dash-header">
                <div className="dash-title">Intelligence Dashboard</div>
                <div className="dash-sub">Real-time analysis across your contact center · Last updated 2 minutes ago</div>
            </div>

            <div className="dash-grid">
                {kpis.map((k) => (
                    <div key={k.label} className="kpi-card" data-icon={k.icon}>
                        <div className="kpi-val" style={k.valColor ? { color: k.valColor } : undefined}>{k.val}</div>
                        <div className="kpi-label">{k.label}</div>
                        <span className={`kpi-delta ${k.dir}`}>{k.delta}</span>
                    </div>
                ))}
            </div>

            <div className="dash-lower">
                <div className="dash-widget">
                    <div className="widget-title">Top Issue Categories — Today</div>
                    {trends.map((t) => (
                        <div key={t.label} className="trend-row">
                            <span className="trend-label">{t.label}</span>
                            <div className="trend-bar-wrap">
                                <div className="trend-bar" style={{ width: `${t.pct}%`, background: t.color }} />
                            </div>
                            <span className="trend-val">{t.pct}%</span>
                        </div>
                    ))}
                </div>

                <div className="dash-widget">
                    <div className="widget-title">Live Alerts</div>
                    {alerts.map((a, i) => (
                        <div key={i} className="alert-item">
                            <div className="alert-dot" style={{ background: a.color }} />
                            <div>
                                <div className="alert-text">{a.text}</div>
                                <div className="alert-meta">{a.meta}</div>
                            </div>
                        </div>
                    ))}
                </div>
            </div>
        </div>
    );
}

// ─── View: Saved Searches ─────────────────────────────────────────────────────

interface SavedViewProps { onNavigate: (v: View) => void }
function SavedView({ onNavigate }: SavedViewProps) {
    const cards = [
        { icon: "📋", name: "Compliance: Missing Disclosure", desc: "Agent did not read required regulatory disclosure during call in Retentions or New Sales queue", freq: "Runs hourly", hits: "8 hits today" },
        { icon: "🎯", name: "Upsell Miss Detector", desc: "Customer had high lifetime value, expressed satisfaction, and call ended without any upsell attempt", freq: "Runs daily", hits: "56 hits yesterday" },
        { icon: "🔁", name: "Repeat Contact — Same Issue", desc: "Customer calling back within 72 hours with same issue type, indicating prior call did not resolve", freq: "Runs daily", hits: "189 hits yesterday" },
        { icon: "🏆", name: "Best Practice Calls", desc: "CSAT ≥ 5, complex issue, resolved on first call — use for agent training library", freq: "Weekly", hits: "44 hits last week" },
        { icon: "🏢", name: "Competitor Intelligence", desc: "Any mention of named competitor brands with context — pricing, feature comparison, or switching intent", freq: "Runs daily", hits: "91 hits yesterday" },
    ];

    return (
        <div className="view active" style={{ flexDirection: "column" }}>
            <div className="dash-header">
                <div className="dash-title">Saved Searches &amp; Alerts</div>
                <div className="dash-sub">Run saved queries on demand or schedule them as nightly alerts</div>
            </div>
            <div className="saved-grid">
                {cards.map((c) => (
                    <div key={c.name} className="saved-card" onClick={() => onNavigate("search")}>
                        <div className="saved-icon">{c.icon}</div>
                        <div className="saved-name">{c.name}</div>
                        <div className="saved-desc">{c.desc}</div>
                        <div className="saved-stats">
                            <span>📅 {c.freq}</span>
                            <span>→ {c.hits}</span>
                        </div>
                    </div>
                ))}
            </div>
        </div>
    );
}

// ─── View: Alerts ─────────────────────────────────────────────────────────────

interface AlertsViewProps { onNavigate: (v: View) => void }
function AlertsView({ onNavigate }: AlertsViewProps) {
    const alerts = [
        {
            dot: "var(--accent)", dotAnim: true,
            sev: "🔴 HIGH — Billing Complaint Spike", age: "14 min ago",
            body: "Billing dispute mentions are up 34% in the last 2 hours compared to the 14-day baseline. 127 calls have been flagged. This pattern correlates with a known billing system incident from 08:42 this morning.",
            btnLabel: "View 127 Calls →",
        },
        {
            dot: "var(--warn)", dotAnim: false,
            sev: "🟡 MEDIUM — Agent Coaching Flag", age: "28 min ago",
            body: "Agent Sarah M. has had 4 escalations in the last 30 minutes — significantly above her baseline of 0.3/hr. Transcript analysis shows repeated use of defensive language when customers challenged charges.",
            btnLabel: "View Agent Calls →",
        },
        {
            dot: "#8a38b2", dotAnim: false,
            sev: "🟣 EMERGING — New Competitor Signal", age: "1 hr ago",
            body: '"SwitchEasy" has been mentioned 47 times today versus a baseline of 3. Customers are referencing their pricing and a "free first month" offer. This may require a competitive response brief.',
            btnLabel: "Explore Signal →",
        },
    ];

    return (
        <div className="view active" style={{ flexDirection: "column" }}>
            <div className="dash-header">
                <div className="dash-title">Active Alerts</div>
                <div className="dash-sub">3 active alerts require your attention</div>
            </div>
            <div style={{ padding: "24px 36px" }}>
                {alerts.map((a, i) => (
                    <div key={i} className="dash-widget" style={{ marginBottom: 16 }}>
                        <div style={{ display: "flex", alignItems: "center", gap: 10, marginBottom: 12 }}>
                            <div
                                style={{
                                    width: 10, height: 10, borderRadius: "50%",
                                    background: a.dot,
                                    animation: a.dotAnim ? "blink 1.2s infinite" : undefined,
                                }}
                            />
                            <div style={{ fontFamily: "'Syne', sans-serif", fontSize: 14, fontWeight: 700 }}>{a.sev}</div>
                            <span style={{ marginLeft: "auto", fontSize: 10, color: "var(--muted)" }}>{a.age}</span>
                        </div>
                        <div style={{ fontSize: 12, lineHeight: 1.7, color: "var(--ink)", marginBottom: 12 }}
                            dangerouslySetInnerHTML={{ __html: a.body.replace(/\d+/g, (n) => `<strong>${n}</strong>`) }}
                        />
                        <button
                            style={{ fontFamily: "'Syne', sans-serif", fontSize: 11, fontWeight: 700, background: "var(--ink)", color: "var(--paper)", border: "none", padding: "8px 18px", borderRadius: 6, cursor: "pointer" }}
                            onClick={() => onNavigate("search")}
                        >
                            {a.btnLabel}
                        </button>
                    </div>
                ))}
            </div>
        </div>
    );
}

// ─── Sidebar ──────────────────────────────────────────────────────────────────

interface SidebarProps {
    activeView: View;
    onNavigate: (v: View) => void;
    activeFilters: string[];
    onToggleFilter: (f: string) => void;
}

function Sidebar({ activeView, onNavigate, activeFilters, onToggleFilter }: SidebarProps) {
    const navItems: { view: View; icon: string; label: string; count: string; countStyle?: React.CSSProperties }[] = [
        { view: "search", icon: "🔍", label: "Search", count: "2.4M" },
        { view: "saved", icon: "⭐", label: "Saved Searches", count: "12" },
        { view: "alerts", icon: "🔔", label: "Alerts", count: "3", countStyle: { background: "#e8d0cc", color: "#e84a2e" } },
    ];

    const quickFilters = [
        { key: "negative", label: "😤 Negative" },
        { key: "escalation", label: "🔺 Escalation" },
        { key: "compliance", label: "📋 Compliance" },
        { key: "repeat", label: "🔁 Repeat Contact" },
    ];

    const pulseStats = [
        { val: "1,847", label: "Calls processed today", delta: "↑ 12% vs yesterday", valColor: undefined, deltaColor: "var(--success)" },
        { val: "23%", label: "Negative sentiment rate", delta: "↑ 4% — billing spike", valColor: "var(--accent)", deltaColor: "var(--warn)" },
        { val: "68%", label: "First call resolution", delta: "↓ 2% — investigate", valColor: "var(--success)", deltaColor: "var(--success)" },
    ];

    return (
        <aside className="sidebar">
            <div className="sidebar-section">
                <div className="sidebar-label">Navigation</div>
                {navItems.map((n) => (
                    <div
                        key={n.view}
                        className={`nav-item${activeView === n.view ? " active" : ""}`}
                        onClick={() => onNavigate(n.view)}
                    >
                        <span className="nav-icon">{n.icon}</span>
                        {n.label}
                        {n.count && (
                            <span className="nav-count" style={n.countStyle}>{n.count}</span>
                        )}
                    </div>
                ))}
            </div>

            <div className="sidebar-section">
                <div className="sidebar-label">Quick Filters</div>
                {quickFilters.map((f) => (
                    <span
                        key={f.key}
                        className={`filter-chip${activeFilters.includes(f.key) ? " selected" : ""}`}
                        onClick={() => onToggleFilter(f.key)}
                    >
                        {f.label}
                    </span>
                ))}
            </div>

            <div className="sidebar-section">
                <div className="sidebar-label">Today's Pulse</div>
                {pulseStats.map((s) => (
                    <div key={s.label} className="mini-stat">
                        <div className="mini-stat-val" style={s.valColor ? { color: s.valColor } : undefined}>{s.val}</div>
                        <div className="mini-stat-label">{s.label}</div>
                        <div className="mini-stat-delta" style={{ color: s.deltaColor }}>{s.delta}</div>
                    </div>
                ))}
            </div>
        </aside>
    );
}

// ─── Root Component ───────────────────────────────────────────────────────────

export default function VoiceIQ() {
    const [activeView, setActiveView] = useState<View>("search");
    const [searchQuery, setSearchQuery] = useState("");
    const [loading, setLoading] = useState(false);
    const [sessionId] = useState(() =>
        crypto.randomUUID()
    );
    const [searchType, setSearchType] = useState<SearchType>("semantic");
    const [hasResults, setHasResults] = useState(false);
    const [summary, setSummary] = useState<SummaryData | null>(null);
    const [selectedCall, setSelectedCall] = useState<Call | null>(null);
    const [activeTab, setActiveTab] = useState<DetailTab>("transcript");
    const [activeFilters, setActiveFilters] = useState<string[]>([]);

    const handleSearch = useCallback(async () => {

        const q = searchQuery.trim();

        if (!q) return;

        try {

            setLoading(true);

            /*
                REQUEST PAYLOAD
            */

            const payload = {
                session_id: sessionId,
                event: "SEARCH_TRIGGERED",
                search_type: searchType,
                query: q,
                timestamp: new Date().toISOString(),
                filters: activeFilters
            };

            console.log("SEARCH REQUEST:", payload);

            /*
                TEMP API DELAY
            */

            await new Promise((resolve) =>
                setTimeout(resolve, 1000)
            );

            /*
                MOCK RESPONSE
            */

            const mockResponse = {
                success: true,
                results: CALLS,
                summary: SUMMARIES[getSummaryKey(q)]
            };

            console.log("SEARCH RESPONSE:", mockResponse);

            /*
                UPDATE UI
            */

            setSummary(mockResponse.summary);

            setHasResults(true);

            setSelectedCall(mockResponse.results[0]);

        } catch (err) {

            console.error("SEARCH ERROR:", err);

        } finally {

            setLoading(false);

        }

    }, [
        searchQuery,
        searchType,
        activeFilters,
        sessionId
    ]);


    const handleUseQuery = useCallback((q: string) => {
        setSearchQuery(q);
        const key = getSummaryKey(q);
        setSummary(SUMMARIES[key]);
        setHasResults(true);
        setSelectedCall(null);
        setActiveView("search");
    }, []);

    const handleSelectCall = useCallback((call: Call) => {
        setSelectedCall(call);
        setActiveTab("transcript");
    }, []);

    const handleToggleFilter = useCallback((f: string) => {
        setActiveFilters((prev) =>
            prev.includes(f) ? prev.filter((x) => x !== f) : [...prev, f]
        );
    }, []);

    const handleNavigate = useCallback((v: View) => {
        setActiveView(v);
    }, []);

    return (
        <>
            <style>{`
        @import url('https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=DM+Mono:ital,wght@0,300;0,400;0,500;1,300&family=Instrument+Serif:ital@0;1&display=swap');

        :root {
          --ink: rgb(0,79,112);
          --paper: #f5f2eb;
          --cream: rgba(221, 238, 245, 0.7);
          --accent: #e84a2e;
          --accent2: #2e6ee8;
          --gold: #c9a84c;
          --muted: #8a8578;
          --border: rgba(0, 79, 112, 0.12);
          --success: #2d8a4e;
          --warn: #d4820a;
          --panel: rgba(240, 247, 252, 0.95);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
          font-family: 'DM Mono', monospace;
          background: var(--paper);
          color: var(--ink);
          min-height: 100vh;
          overflow-x: hidden;
        }

        .shell {
          display: grid;
          grid-template-columns: 260px 1fr;
          grid-template-rows: 1fr;
          min-height: 100vh;
        }

        .topbar {
          grid-column: 1 / -1;
          background: linear-gradient(135deg, rgb(0, 79, 112) 0%, rgb(81, 145, 205) 100%);
          display: flex;
          align-items: center;
          padding: 0 24px;
          gap: 16px;
          border-bottom: 2px solid var(--accent);
          position: sticky;
          top: 0;
          z-index: 100;
        }

        .logo { font-family: 'Syne', sans-serif; font-weight: 800; font-size: 20px; color: var(--paper); letter-spacing: -0.5px; display: flex; align-items: center; gap: 8px; }
        .logo-dot { color: var(--accent); }

        .topbar-center { flex: 1; max-width: 600px; margin: 0 auto; }

        .global-search {
          width: 100%; background: rgba(255,255,255,0.07); border: 1px solid rgba(255,255,255,0.15);
          border-radius: 6px; padding: 8px 14px; color: #fff; font-family: 'DM Mono', monospace;
          font-size: 13px; outline: none; transition: border-color 0.2s;
        }
        .global-search::placeholder { color: rgba(255,255,255,0.35); }
        .global-search:focus { border-color: var(--accent); }

        .topbar-right { margin-left: auto; display: flex; align-items: center; gap: 12px; font-size: 12px; color: rgba(255,255,255,0.5); }

        .badge { background: var(--accent); color: #fff; font-size: 10px; padding: 2px 7px; border-radius: 20px; font-weight: 700; letter-spacing: 0.5px; }

        .sidebar { background: rgba(221, 238, 245, 0.7); border-right: 1px solid var(--border); padding: 20px 0; overflow-y: auto; }
        .sidebar-section { margin-bottom: 28px; padding: 0 16px; }
        .sidebar-label { font-family: 'Syne', sans-serif; font-size: 10px; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; color: var(--muted); margin-bottom: 10px; }

        .nav-item { display: flex; align-items: center; gap: 10px; padding: 8px 10px; border-radius: 6px; cursor: pointer; font-size: 13px; color: var(--ink); transition: all 0.15s; margin-bottom: 2px; border: 1px solid transparent; }
        .nav-item:hover { background: rgba(0,0,0,0.05); }
        .nav-item.active {background: linear-gradient(135deg, rgb(0, 79, 112) 0%, rgb(81, 145, 205) 100%); color: var(--paper); border-color: var(--ink); }
        .nav-icon { font-size: 15px; }
        .nav-count { margin-left: auto; font-size: 10px; background: var(--border); padding: 1px 6px; border-radius: 10px; }
        .nav-item.active .nav-count { background: rgba(255,255,255,0.15); color: rgba(255,255,255,0.7); }

        .filter-chip { display: inline-flex; align-items: center; gap: 5px; background: var(--panel); border: 1px solid var(--border); padding: 4px 10px; border-radius: 20px; font-size: 11px; cursor: pointer; margin: 3px 3px 3px 0; transition: all 0.15s; }
        .filter-chip:hover { border-color: var(--accent); color: var(--accent); }
        .filter-chip.selected { background: var(--accent); color: #fff; border-color: var(--accent); }

        .mini-stat { background: var(--panel); border: 1px solid var(--border); border-radius: 8px; padding: 10px 12px; margin-bottom: 8px; }
        .mini-stat-val { font-family: 'Syne', sans-serif; font-size: 22px; font-weight: 800; color: var(--ink); }
        .mini-stat-label { font-size: 10px; color: var(--muted); margin-top: 2px; }
        .mini-stat-delta { font-size: 10px; color: var(--success); margin-top: 4px; }

        .main { background: var(--panel); overflow-y: auto; display: flex; flex-direction: column; }

        .view { display: none; flex-direction: column; height: 100%; }
        .view.active { display: flex; }

        
        .search-hero::before { content: ''; position: absolute; top: -40px; right: -40px; width: 220px; height: 220px; border-radius: 50%; border: 40px solid rgba(232,74,46,0.1); }
        .search-hero::after  { content: ''; position: absolute; bottom: -60px; left: 40%; width: 140px; height: 140px; border-radius: 50%; background: rgba(46,110,232,0.06); }

        .search-title {
  font-family: 'Syne', sans-serif;
  font-size: 38px;
  font-weight: 500;
  color: white;
  margin-bottom: 8px;
}
 
        .search-sub { font-size: 12px; color: rgba(255,255,255,0.72); font-size:16px; margin-bottom: 22px; }
        
          .search-hero {
  background: linear-gradient(135deg, rgb(0, 79, 112) 0%, rgb(81, 145, 205) 100%);
  padding: 40px 36px 70px;
  position: relative;
  overflow: hidden;
}
 
.search-box-wrap {
  position: relative;
  width: 100%;
  max-width: 850px;
  margin-top: 20px;
}
 
.main-search {
  width: 100%;
  height: 62px;
  background: #ffffff;
  border: 4px solid rgba(255,255,255,0.7);
  border-radius: 18px;
  padding: 0 85px 0 24px;
  font-family: 'Syne', sans-serif;
  font-size: 20px;
  color: #676666;
  outline: none;
  box-shadow:
    0 10px 25px rgba(0,0,0,0.15),
    inset 0 1px 2px rgba(255,255,255,0.3);
  transition: all 0.25s ease;
}
 
.main-search::placeholder {
  color: #ddd8d8;
  font-size: 18px;
}
 
.main-search:focus {
  border-color: #7fc4ff;
  box-shadow:
    0 0 0 4px rgba(127,196,255,0.25),
    0 10px 30px rgba(0,0,0,0.18);
}
 
.search-btn {
  position: absolute;
  right: 8px;
  top: 50%;
  transform: translateY(-50%);
  width: 56px;
  height: 46px;
  border-radius: 12px;
  border: none;
  background:linear-gradient(135deg, rgb(0, 79, 112) 0%, rgb(81, 145, 205) 100%);
  color: white;
  font-size: 22px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s ease;
}
 
.search-btn:hover {
  transform: translateY(-50%) scale(1.05);
}

        .search-type-row { display: flex; gap: 8px; margin-top: 14px; flex-wrap: wrap; }
        .type-pill { font-size: 11px; padding: 5px 12px; border-radius: 20px; cursor: pointer; border: 1px solid rgba(255,255,255,0.15); color: rgba(255,255,255,0.6); transition: all 0.15s; }
        .type-pill.active { background: var(--accent); border-color: var(--accent); color: #fff; }
        .type-pill:hover:not(.active) { border-color: rgba(255,255,255,0.4); color: #fff; }

        .suggestion-row { display: flex; gap: 10px; padding: 18px 36px; border-bottom: 1px solid var(--border); overflow-x: auto; background: rgba(221, 238, 245, 0.7); flex-shrink: 0; }
        .suggestion-row::-webkit-scrollbar { height: 0; }
           
        .suggestion-scroll {
  display: flex;
  gap: 10px;
  overflow-x: auto;
  flex-wrap: nowrap;
  scrollbar-width: none;
  width: 100%;
}
 
.suggestion-scroll::-webkit-scrollbar {
  display: none;
}
 
.suggest-chip {
  white-space: nowrap;
  font-size: 11px;
  padding: 8px 16px;
  background: rgba(255,255,255,0.95);
  border: 1px solid rgba(0, 79, 112, 0.12);
  border-radius: 999px;
  cursor: pointer;
  transition: all 0.2s ease;
  color: #4c5b6b;
  flex-shrink: 0;
  font-weight: 500;
  box-shadow: 0 2px 6px rgba(0,0,0,0.04);
}
 
.suggest-chip:hover {
  background: #0b4f70;
  color: white;
  transform: translateY(-1px);
}
        .suggest-chip { white-space: nowrap; font-size: 11px; padding: 6px 14px; background: var(--panel); border: 1px solid var(--border); border-radius: 20px; cursor: pointer; transition: all 0.15s; color: var(--muted); flex-shrink: 0; }
        .suggest-chip:hover { border-color: var(--accent2); color: var(--accent2); background: rgba(46,110,232,0.05); }

        .filter-bar { display: flex; align-items: center; gap: 10px; padding: 14px 36px; border-bottom: 1px solid var(--border); background: var(--panel); flex-wrap: wrap; flex-shrink: 0; }
        .filter-label { font-size: 10px; font-weight: 600; letter-spacing: 1.5px; text-transform: uppercase; color: var(--muted); margin-right: 4px; }
        select.filter-select { font-family: 'DM Mono', monospace; font-size: 11px; background: var(--panel); border: 1px solid var(--border); border-radius: 6px; padding: 5px 10px; color: var(--ink); cursor: pointer; outline: none; }
        .result-count { margin-left: auto; font-size: 11px; color: var(--muted); }

        .results-area { display: grid; grid-template-columns: 1fr 380px; flex: 1; overflow: hidden; }
        .results-list { overflow-y: auto; padding: 20px 24px; border-right: 1px solid var(--border); }

        .ai-summary {background: linear-gradient(135deg, rgb(0, 79, 112) 0%, rgb(81, 145, 205) 100%); border: 1px solid rgba(232,74,46,0.3); border-radius: 10px; padding: 18px; margin-bottom: 20px; position: relative; overflow: hidden; }
        .ai-summary::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 2px; background: linear-gradient(90deg,var(--accent),var(--accent2)); }
        .ai-summary-header { display: flex; align-items: center; gap: 8px; margin-bottom: 12px; }
        .ai-tag { font-family: 'Syne', sans-serif; font-size: 9px; font-weight: 700; letter-spacing: 2px; color: var(--accent); text-transform: uppercase; }
        .ai-summary-body { font-size: 12px; color: rgba(245,242,235,0.85); line-height: 1.7; }
        .ai-insight-chips { display: flex; gap: 6px; margin-top: 12px; flex-wrap: wrap; }
        .insight-chip { font-size: 10px; padding: 3px 10px; border-radius: 20px; border: 1px solid rgba(255,255,255,0.1); color: rgba(255,255,255,0.6); }
        .insight-chip.red   { border-color: rgba(232,74,46,0.4);  color: #e87a6a; background: rgba(232,74,46,0.08); }
        .insight-chip.blue  { border-color: rgba(46,110,232,0.4); color: #7aabe8; background: rgba(46,110,232,0.08); }
        .insight-chip.green { border-color: rgba(45,138,78,0.4);  color: #7ae8a0; background: rgba(45,138,78,0.08); }

        .call-card { background: #fff; border: 1px solid var(--border); border-radius: 10px; padding: 16px; margin-bottom: 12px; cursor: pointer; transition: all 0.2s; position: relative; overflow: hidden; }
        .call-card::before { content: ''; position: absolute; left: 0; top: 0; bottom: 0; width: 3px; background: var(--border); transition: background 0.2s; }
        .call-card:hover { border-color: var(--accent2); box-shadow: 0 4px 16px rgba(0,0,0,0.08); }
        .call-card:hover::before { background: var(--accent2); }
        .call-card.selected { border-color: var(--accent2); box-shadow: 0 4px 20px rgba(46,110,232,0.15); }
        .call-card.selected::before { background: var(--accent2); }

        .card-top { display: flex; align-items: flex-start; gap: 10px; margin-bottom: 10px; }
        .agent-avatar { width: 34px; height: 34px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-family: 'Syne', sans-serif; font-weight: 800; font-size: 12px; flex-shrink: 0; }
        .card-meta { flex: 1; }
        .card-id { font-size: 10px; color: var(--muted); margin-bottom: 2px; }
        .card-agent { font-family: 'Syne', sans-serif; font-size: 13px; font-weight: 700; }
        .card-date { font-size: 10px; color: var(--muted); }

        .sentiment-badge { font-size: 10px; padding: 3px 9px; border-radius: 20px; font-weight: 600; flex-shrink: 0; }
        .sent-negative { background: rgba(232,74,46,0.1); color: var(--accent); border: 1px solid rgba(232,74,46,0.2); }
        .sent-positive { background: rgba(45,138,78,0.1);  color: var(--success); border: 1px solid rgba(45,138,78,0.2); }
        .sent-neutral  { background: rgba(138,133,120,0.1); color: var(--muted); border: 1px solid var(--border); }

        .card-snippet { font-size: 12px; color: var(--muted); line-height: 1.6; margin-bottom: 10px; }
        .card-tags { display: flex; gap: 6px; flex-wrap: wrap; }
        .tag { font-size: 10px; padding: 2px 8px; border-radius: 4px; border: 1px solid var(--border); color: var(--muted); background:rgba(221, 238, 245, 0.7); }
        .tag.compliance { background: rgba(212,130,10,0.1); border-color: rgba(212,130,10,0.3); color: var(--warn); }
        .tag.churn      { background: rgba(232,74,46,0.1);  border-color: rgba(232,74,46,0.2);  color: var(--accent); }
        .tag.escalation { background: rgba(138,56,178,0.1); border-color: rgba(138,56,178,0.2); color: #8a38b2; }

        .card-stats { display: flex; gap: 14px; margin-top: 10px; padding-top: 10px; border-top: 1px solid var(--border); }
        .card-stat { font-size: 10px; color: var(--muted); display: flex; align-items: center; gap: 4px; }
        .card-stat strong { color: var(--ink); }

        .detail-panel { overflow-y: auto; background: #fff; display: flex; flex-direction: column; }
        .detail-header { padding: 20px; border-bottom: 1px solid var(--border); background: var(--panel); flex-shrink: 0; }
        .detail-call-id { font-size: 10px; color: var(--muted); margin-bottom: 4px; }
        .detail-title { font-family: 'Syne', sans-serif; font-size: 16px; font-weight: 800; margin-bottom: 8px; }
        .detail-meta-row { display: flex; gap: 14px; flex-wrap: wrap; }
        .detail-meta-item { font-size: 11px; color: var(--muted); display: flex; align-items: center; gap: 4px; }

        .detail-tabs { display: flex; border-bottom: 1px solid var(--border); flex-shrink: 0; background: var(--panel); }
        .detail-tab { font-size: 11px; padding: 10px 18px; cursor: pointer; border-bottom: 2px solid transparent; color: var(--muted); transition: all 0.15s; font-weight: 500; }
        .detail-tab.active { color: var(--accent2); border-bottom-color: var(--accent2); }
        .detail-tab:hover:not(.active) { color: var(--ink); }
        .detail-body { padding: 20px; flex: 1; overflow-y: auto; }

        .transcript-line { display: flex; gap: 12px; margin-bottom: 16px; animation: fadeIn 0.3s ease; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(4px); } to { opacity: 1; transform: translateY(0); } }
        .line-speaker { font-size: 10px; font-weight: 700; width: 52px; flex-shrink: 0; padding-top: 3px; letter-spacing: 0.5px; text-transform: uppercase; }
        .speaker-agent { color: var(--accent2); }
        .speaker-cust  { color: var(--accent); }
        .line-bubble { flex: 1; background: var(--panel); border: 1px solid var(--border); border-radius: 8px; padding: 10px 13px; font-size: 12px; line-height: 1.7; color: var(--ink); }
        .line-bubble.agent { background: rgba(46,110,232,0.05); border-color: rgba(46,110,232,0.15); }
        .line-bubble.cust  { background: rgba(232,74,46,0.04);  border-color: rgba(232,74,46,0.12); }
        .line-time { font-size: 9px; color: var(--muted); margin-top: 4px; }
        .emotion-indicator { font-size: 10px; margin-top: 4px; color: var(--muted); }

        .analysis-block { background: var(--panel); border: 1px solid var(--border); border-radius: 8px; padding: 14px; margin-bottom: 12px; }
        .analysis-title { font-family: 'Syne', sans-serif; font-size: 11px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: var(--muted); margin-bottom: 10px; }
        .analysis-text { font-size: 12px; line-height: 1.7; color: var(--ink); }
        .score-bar { margin-bottom: 10px; }
        .score-label { display: flex; justify-content: space-between; font-size: 11px; color: var(--muted); margin-bottom: 4px; }
        .score-track { height: 6px; background: var(--border); border-radius: 3px; overflow: hidden; }
        .score-fill { height: 100%; border-radius: 3px; transition: width 1s ease; }
        .moment-item { display: flex; gap: 10px; padding: 8px 0; border-bottom: 1px solid var(--border); font-size: 12px; align-items: flex-start; }
        .moment-item:last-child { border-bottom: none; }
        .moment-time { font-size: 10px;background: linear-gradient(135deg, rgb(0, 79, 112) 0%, rgb(81, 145, 205) 100%); color: var(--paper); padding: 2px 7px; border-radius: 4px; flex-shrink: 0; margin-top: 1px; }
        .moment-text { color: var(--ink); line-height: 1.5; }
        .moment-type { font-size: 10px; color: var(--muted); margin-top: 2px; }

        .empty-state { display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; padding: 40px; text-align: center; color: var(--muted); }
        .empty-icon  { font-size: 48px; margin-bottom: 16px; opacity: 0.4; }
        .empty-title { font-family: 'Syne', sans-serif; font-size: 16px; font-weight: 700; color: var(--ink); margin-bottom: 8px; }
        .empty-text  { font-size: 12px; line-height: 1.7; max-width: 260px; }

        .dash-header { padding: 28px 36px 20px; border-bottom: 1px solid var(--border); background: var(--panel); }
        .dash-title  { font-family: 'Instrument Serif', serif; font-size: 24px; font-style: italic; margin-bottom: 4px; }
        .dash-sub    { font-size: 12px; color: var(--muted); }

        .dash-grid { display: grid; grid-template-columns: repeat(4,1fr); gap: 16px; padding: 24px 36px; }
        .kpi-card { background: #fff; border: 1px solid var(--border); border-radius: 10px; padding: 18px; position: relative; overflow: hidden; }
        .kpi-card::after { content: attr(data-icon); position: absolute; right: 14px; top: 14px; font-size: 22px; opacity: 0.2; }
        .kpi-val   { font-family: 'Syne', sans-serif; font-size: 30px; font-weight: 800; line-height: 1; margin-bottom: 4px; }
        .kpi-label { font-size: 11px; color: var(--muted); margin-bottom: 8px; }
        .kpi-delta { font-size: 10px; display: inline-flex; align-items: center; gap: 3px; padding: 2px 8px; border-radius: 20px; }
        .kpi-delta.up   { background: rgba(45,138,78,0.1); color: var(--success); }
        .kpi-delta.down { background: rgba(232,74,46,0.1); color: var(--accent); }

        .dash-lower  { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; padding: 0 36px 24px; }
        .dash-widget { background: #fff; border: 1px solid var(--border); border-radius: 10px; padding: 18px; }
        .widget-title { font-family: 'Syne', sans-serif; font-size: 11px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: var(--muted); margin-bottom: 14px; }

        .trend-row     { display: flex; align-items: center; gap: 10px; margin-bottom: 10px; font-size: 12px; }
        .trend-label   { flex: 1; color: var(--ink); }
        .trend-bar-wrap{ width: 120px; height: 8px; background: var(--border); border-radius: 4px; overflow: hidden; }
        .trend-bar     { height: 100%; border-radius: 4px; }
        .trend-val     { width: 32px; text-align: right; color: var(--muted); font-size: 11px; }

        .alert-item       { display: flex; gap: 10px; padding: 10px 0; border-bottom: 1px solid var(--border); align-items: flex-start; }
        .alert-item:last-child { border-bottom: none; }
        .alert-dot  { width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0; margin-top: 4px; }
        .alert-text { font-size: 12px; color: var(--ink); line-height: 1.5; }
        .alert-meta { font-size: 10px; color: var(--muted); margin-top: 2px; }

        .saved-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 16px; padding: 24px 36px; }
        .saved-card { background: #fff; border: 1px solid var(--border); border-radius: 10px; padding: 18px; cursor: pointer; transition: all 0.2s; }
        .saved-card:hover { border-color: var(--accent2); box-shadow: 0 4px 16px rgba(0,0,0,0.08); }
        .saved-icon  { font-size: 24px; margin-bottom: 10px; }
        .saved-name  { font-family: 'Syne', sans-serif; font-size: 14px; font-weight: 700; margin-bottom: 6px; }
        .saved-desc  { font-size: 11px; color: var(--muted); line-height: 1.6; margin-bottom: 12px; }
        .saved-stats { display: flex; gap: 12px; font-size: 10px; color: var(--muted); }

        .pattern-builder { background: linear-gradient(135deg, rgb(0, 79, 112) 0%, rgb(81, 145, 205) 100%); border-radius: 10px; padding: 20px; margin-bottom: 20px; }
        .pattern-header  { display: flex; align-items: center; gap: 8px; margin-bottom: 14px; }
        .pattern-steps   { display: flex; gap: 8px; align-items: center; flex-wrap: wrap; }
        .pattern-step    { background: rgba(255,255,255,0.08); border: 1px solid rgba(255,255,255,0.15); border-radius: 8px; padding: 8px 14px; font-size: 11px; color: rgba(255,255,255,0.8); display: flex; align-items: center; gap: 6px; cursor: pointer; transition: all 0.15s; }
        .pattern-step:hover { background: rgba(255,255,255,0.13); }
        .step-num   { color: var(--accent); font-weight: 700; font-size: 10px; }
        .pattern-arrow { color: rgba(255,255,255,0.2); font-size: 16px; }

        ::-webkit-scrollbar       { width: 5px; height: 5px; }
        ::-webkit-scrollbar-track { background: transparent; }
        ::-webkit-scrollbar-thumb { background: var(--border); border-radius: 10px; }
        ::-webkit-scrollbar-thumb:hover { background: var(--muted); }

        @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0.3} }

        @media (max-width: 1100px) {
          .results-area { grid-template-columns: 1fr; }
          .detail-panel { display: none; }
          .dash-grid    { grid-template-columns: repeat(2,1fr); }
          .saved-grid   { grid-template-columns: repeat(2,1fr); }
        }
        @media (max-width: 800px) {
          .shell      { grid-template-columns: 1fr; }
          .sidebar    { display: none; }
          .dash-grid  { grid-template-columns: 1fr 1fr; }
          .dash-lower { grid-template-columns: 1fr; }
        }
      `}</style>

            <div className="shell">

                {/* Sidebar */}
                <Sidebar
                    activeView={activeView}
                    onNavigate={handleNavigate}
                    activeFilters={activeFilters}
                    onToggleFilter={handleToggleFilter}
                />

                {/* Main content */}
                <main className="main">
                    {activeView === "search" && (
                        <SearchView
                            searchQuery={searchQuery}
                            setSearchQuery={setSearchQuery}
                            searchType={searchType}
                            setSearchType={setSearchType}
                            hasResults={hasResults}
                            summary={summary}
                            selectedCall={selectedCall}
                            activeTab={activeTab}
                            onSearch={handleSearch}
                            onUseQuery={handleUseQuery}
                            onSelectCall={handleSelectCall}
                            onTabChange={setActiveTab}
                        />
                    )}
                    {activeView === "dashboard" && <DashboardView />}
                    {activeView === "saved" && <SavedView onNavigate={handleNavigate} />}
                    {activeView === "alerts" && <AlertsView onNavigate={handleNavigate} />}
                </main>
            </div>
        </>
    );
}
