## Note
This is for things that don't need to be secure at all. If you need something for something like a customer database, please use UUIDs.

## Usage
Basic usage:
```
import SeqIDs from "seq-ids";

const seq = new SeqIDs();

const num = seq.new();
console.log(num); // 0

seq.new(); // == 1
seq.new(); // == 2
```

Also includes the ability to specify a base:
```
const seq = new SeqIDs(16);
```

And the ability to reserve a certain ID:
```
const seq = new SeqIDs(36); // <= IDs generated will use 0-9 and the whole lowercase alphabet

seq.new(); // 0
// ... imagine we call seq.new a bunch of times ...
seq.new(); // 8
seq.new(); // 9
seq.new(); // a
seq.new(); // b
// If seq is called through new SeqIDs(36), it will use all numbers and lowercase letters.

seq.reserve("reserved");
//If seq gets to "reserved", it will skip over it.
```

## Docs

___

**new SeqIDs**(`base`?: *number*)

Creates a new sequential ID generator. `base` is the base to use for IDs (defaults to 10 if omitted).

___

**new**(): *string | number*

Generates a new ID. Will be numeric if outBase is not specified in the constructor
or is 10, otherwise it will be an alphanumeric string.

___

**reserve**(`id`: string | number): *string | number*

Reserves an ID so that it can't be generated. It will just be skipped if the generator gets to it. Returns the ID passed in.

___

**reserve**(`...ids`: (string | number)[]): *(string | number)[]*

Reserves all of the IDs passed in as arguments.