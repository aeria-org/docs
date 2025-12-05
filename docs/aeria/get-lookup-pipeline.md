# `getLookupPipeline()`
>`getLookupPipeline(description: Description, options?: BuildLookupPipelineOptions) => Document[]`

This function builts a MongoDB aggregation pipeline using the internal reference resolution API. It can be used to iterate documents lazily with `.next()` instead of returning paginated arrays.

### Example

The example below gets the aggregation pipeline for retrieving documents of the `person` collection with references being populated with objects instead of ObjectIds. The value of `pipeline` will be an array containing MongoDB aggregation stages.

Instead of retrieving all documents in a single call using [`getAll()`](/aeria/builtins/functions#getall) (that also deep-populates references), the code in this example iterates documents one by one, and can be used to traverse all the collection in a memory efficient way.

```ts
const pipeline = await getLookupPipeline(context.collections.person.description, {
  memoize: context.collections.person.description.$id,
  project: payload.populate || project,
})

const it = context.collection.model.aggregate(pipeline)

for await ( const document of it ) {
  // {
  //   name: 'John',
  //   pet: {
  //     _id: ObjectId('...'),
  //     name: 'Thor'
  //   }
  // }
  console.log(document)
}
```

