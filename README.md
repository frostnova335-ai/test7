import searchResponse from "../data/searchResponse.json";

const [apiData, setApiData] = useState<any>(null);


useEffect(() => {
  setApiData(searchResponse.response);
}, []);



apiData.search
apiData.suggestions
apiData.quick_filters
apiData.ai_summary
apiData.interactions


const handleUseQuery = useCallback((q: string) => {
    setSearchQuery(q);

    setSummary(apiData?.ai_summary?.summary_text || "");

    setHasResults(true);
    setSelectedCall(null);
    setActiveView("search");
}, [apiData]);



apiData?.suggestions?.map((item: string) => (
    <div
        key={item}
        className="suggest-chip"
        onClick={() => handleUseQuery(item)}
    >
        {item}
    </div>
))






apiData?.quick_filters?.map((filter:any) => (
    <div
        key={filter.label}
        className="filter-chip"
    >
        {filter.label} ({filter.count})
    </div>
))



{apiData?.ai_summary?.summary_text}


{apiData?.ai_summary?.title}


apiData?.ai_summary?.metrics?.map((metric:any)=>(
   <span
      key={metric.label}
      className={`insight-chip ${metric.type}`}
   >
      {metric.label}
   </span>
))



{apiData?.search?.total_results} results


apiData?.interactions?.map((call:any) => (
   <CallCard
      key={call.call_id}
      call={call}
      onClick={() => handleSelectCall(call)}
   />
))


selectedCall.customer_name
selectedCall.summary
selectedCall.queue
selectedCall.duration
selectedCall.sentiment



selectedCall.detail_panel.transcript.map((line:any)=>(
    <div key={line.time}>
        <strong>{line.speaker}</strong>
        {line.message}
    </div>
))


selectedCall.detail_panel.analysis.conversation_summary


selectedCall.detail_panel.analysis.quality_scores.empathy

selectedCall.detail_panel.analysis.quality_scores.compliance

selectedCall.detail_panel.analysis.quality_scores.pace

selectedCall.detail_panel.analysis.quality_scores.fcr


selectedCall.detail_panel.moments.map((moment:any)=>(
   <div key={moment.time}>
      {moment.time}
      {moment.type}
      {moment.text}
   </div>
))




apiData?.todays_pulse?.calls_processed

apiData?.todays_pulse?.negative_sentiment_rate

apiData?.todays_pulse?.first_call_resolution

apiData?.todays_pulse?.alerts



