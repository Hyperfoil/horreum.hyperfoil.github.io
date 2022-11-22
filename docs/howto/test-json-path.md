# test JSON Path on Dataset How to

 Datasets transformed from Runs are available to be used in Reports or change detection. Manipulating Run data that has relevant data into arrays or scalar value ready for these tasks. The ability to query JSON data and test the search paths is available using the Datasets view. The view provides immediate feedback on the success or otherwise of the query.

<div class="screenshot"><img src="/assets/images/datasets/json_query_path_testing.png" /></div>
 
 Query paths can be tested in the following modes. With varying relevance to the execution.

1) 'js' JavaScript syntax
2) 'jsonb_path_query_first' scalar value result
3) 'jsonb_path_query_array' array result

 Only option 2 and 3 provide jsonb query datatype [compatability](https://www.postgresql.org/docs/current/datatype-json.html) provided by PostgreSQL database. Only PostgreSQL types are available at execution time during Run transformation into Datasets.

<div class="screenshot"><img src="/assets/images/datasets/json_path_query_drop_down_list.png" /></div>

