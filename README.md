# Collection-softremovable

Add soft remove to collections

## Usage

```js
Posts = new Mongo.Collection('posts');

//Default options
Posts.attachBehaviour('softRemovable');

//Custom options
Posts.attachBehaviour('softRemovable', {
  removed: 'deleted',
  removedAt: 'deletedAt',
  removedBy: false,
  restoredAt: 'undeletedAt',
  restoredBy: false
});

// Soft remove document by _id
Posts.softRemove({_id: 'BFpDzGuWG8extPwrE'});

// Restore document by _id
Posts.restore('BFpDzGuWG8extPwrE');

// Find all posts that are removed
Posts.find({removed: true});

// Find all posts including removed
Posts.find({}, {removed: true});
```

## Options

Available options are:

`removed, removedAt, removedBy, restoredAt, restoredBy`

Valid values are:

`'string'` will be used as field name.  
`false` field will be omitted.
