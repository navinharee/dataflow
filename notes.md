🔹 What wait_until_finished=True means

Normally, DataflowStartFlexTemplateOperator launches the Dataflow job and returns immediately after the API call succeeds (job created).

✅ If you set wait_until_finished=True:
The operator will poll Dataflow until the job reaches a terminal state (JOB_STATE_DONE, FAILED, CANCELLED, etc.).
Only then will Airflow mark the task as success/failure.

❌ If you don’t set it (or your version doesn’t support it):
The operator will mark the Airflow task as success as soon as the job is launched (even though the Dataflow job may still be running in GCP). You then need a sensor to wait on job completion (like DataflowJobStatusSensor).
