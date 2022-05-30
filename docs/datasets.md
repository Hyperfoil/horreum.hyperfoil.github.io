# Transform Runs to Datasets

Horreum stores data in json format. Once it gets uploaded to repository it becomes a **Run**.
If one run represents multiple tests that need to be analyzed separately then it is 
recommended to split it by **Datasets**.

We assume that you've already [created a test](/docs/create_test.html), [uploaded](/docs/upload.html) some data and [defined the Schema](/docs/customize_views.html).
In this example we use test `acme-regression` with the basic schema `acme-schema` and uploaded json:

```json
{
 "$schema": "urn:acme-schema:1.0",
 "testName": [
   "Test CPU1",
   "Test CPU2",
   "Test CPU3"
 ],
 "throughput": [
   0.1,
   0.2,
   0.3
 ]
}
```

<div class="screenshot"><img src="/assets/images/datasets/raw_input.png"></div>

## How to create a transformer?
Problem is how to get _DataSets_ from the raw input so each _testName_ and _throughput_ goes to a separate set?

First we need to define the **Target schema URI** like `urn:acme-sub-schema:1.0` that will be added to each **Dataset** by the transformer.

Then in `acme-schema` we can define `CpuDatasetTransformer`. It contains extractors _testName_ and _throughput_ 
that will get the values from the raw json and put it into the **Combination function**. 
As a result, the transformer will return the array of objects each of them represents DataSet.

<div class="screenshot"><img src="/assets/images/datasets/transformer_setup.png"></div>


## How to use transformers in tests?
After configuration of transformers is done let's assign it to `acme-regression` test.

Tests > Transformers

<div class="screenshot"><img src="/assets/images/datasets/test_transformers.png"></div>

Press _Recalculate datasets_ and then press _Dataset list_ to see the results.
You will get 3 _Datasets_. Each contains a separate test result.

<div class="screenshot"><img src="/assets/images/datasets/datasets.png"></div>

## How to define and use labels for target schema?

Finally, in the `acme-sub-schema` we can define the labels _testname_ and _throughput_ to use it as a 
**fingerprint** and **change** detection data points in the test later.

<div class="screenshot"><img src="/assets/images/datasets/labels.png"></div>

The last we need to configure is change detection **variables**.

Test > Change 
<div class="screenshot"><img src="/assets/images/datasets/variables.png "></div>

After saving and recalculation you will see the new data-points in **Changes**

<div class="screenshot"><img src="/assets/images/datasets/change.png"></div>

So we transformed the **Run** from the batch results arrays to an array of **Datasets**. 
Then we extracted data by the provided **Labels** and the change **Variables** and used it for change detection.

