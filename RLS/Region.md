[Region] IN 
CALCULATETABLE(
        VALUES ( 'fact_RLS_RenalCare'[Region] )
        , 'fact_RLS_RenalCare'[Email Address] = USERNAME()
)
