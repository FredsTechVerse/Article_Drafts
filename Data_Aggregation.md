## COUNT METHOD

- Used to count the number of documents present in a collection.
eg 
```js
 const aggregateCourses = async (req, res) => {
  try {
    const coursesCount = await Course.count();
    console.log({ coursesCount });
    res.sendStatus(200);
  } catch (err) {
    console.log(`Course aggregation error ${JSON.stringify(err)}`);
    handleError(err, res);
  }
};
```

## Mongoose Data Aggregation
- Data aggregation involves performing complex operations on data stored in MongoDB collections. Aggregation facilitates processing, data transformation, and deriving insights from documents.
- Mongoose provides aggregation capabilities through the `.aggregate()` method.
- **Pipeline**: Its simply a sequence of stages where each stage is a processing step. Multiple stages can be combined to create a pipeline.

### MOST COMMONLY USED OPERATORS

- **$project**: Used to select the specific fields we need.

- **$match**: Filters documents based on criteria, similar to `find()`. It selects documents meeting specific conditions.

- **$group**: Groups documents based on specified keys. Often followed by accumulator operators to calculate data within groups.While grouping say units , I can accumulate the member units props into an array of say member units. An accumulator object is somehow involved in the mix.
```js
  {
        $group: {
          _id: "$courseInformation.courseTitle",
          memberUnits: {
            $push: {
              unitCode: "$unitCode",
            },
          },
          unitCount: { $sum: 1 },
        },
      },
```

- **$sort**: Sorts documents by one or more fields. Now that we have been able to maybe find the count of the units per course , we can now simply sort by the one with the most count tukienda hivo.

- **$limit**: Limits the number of documents passing through the pipeline.

- **$skip**: Skips a certain number of documents in the pipeline.

- **$lookup**: Adds a new array field to each input document.Almost similar to populating. Compares the localField and the foreignField then imports data as specified without altering say the courseID which i was using to fetch the course information. 

```js 
 $lookup: {
          from: "courses",
          localField: "course", 
          foreignField: "_id",
          as: "courseInformation",
        },
```
- **$unwind**: Splits array fields into separate documents, useful for further array operations. Without it , the new courseInformation field will read as an [object] array
```js
 {
        $unwind: "$courseInformation",
      }
```

- **$addFields**: Adds new fields to documents, similar to `$project` but for adding fields.
- **$facet**: Applies multiple aggregation pipelines to the same set of documents. Useful for computing multiple aggregations in one query.

# Basic example - Note that each object is a stage in the data aggregation.

-  We can have different items with different colors ..... We first identify the books among the items , group them by color eg red books together etc and count each heap.Then return the computed value.

```js 
const result = await Items.aggregate([
  { $match: { type: 'book' } },
  { $group: { _id: '$color', totalBooks: { $sum: 1 } } },
  { $sort: { totalBooks: -1 } },
  { $limit: 5 }
]);
```


# USE CASE

- Data aggregation is primarily designed to perform complex data processing and transformation tasks on large datasets. 
- The main purposes of data aggregation are:

- **Data Transformation**: Aggregation allows you to reshape, combine, and transform data from multiple documents into a new format that suits your needs. This is especially useful for deriving insights, generating reports, and performing calculations on aggregated data.

- **Summarization**: Aggregation enables summarizing data by calculating sums, averages, counts, and other aggregations across multiple documents. This is helpful for generating meaningful statistics and insights.

- **Grouping**: Aggregation can group documents based on certain criteria, enabling you to analyze data within specific categories or segments. This is essential for segmenting and understanding data based on different dimensions.

- **Joining Data**: Through the $lookup stage, aggregation can be used to combine data from different collections, providing the capability to perform joins similar to relational databases.

- **Data Cleansing**: Aggregation pipelines can help clean and transform data by filtering out irrelevant or incorrect records, fixing inconsistencies, and generating clean, usable data.

- **Conditional Processing**: Aggregation allows for conditional processing, where different actions are taken based on the data's values. This can be used to create conditional fields or categorize data based on certain conditions.

- **Custom Calculations**: Aggregation allows you to perform custom calculations and transformations that might not be achievable using standard query methods.

