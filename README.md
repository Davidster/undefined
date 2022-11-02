# undefined
A project to turn a file of JSON responses into TypeScript types

## Warning on code
I haven't really tried to organize this code.  I made this code strictly as i
learned more about the problem space.  So the code looks like exploratory code,
not production ready code.

To me, it seems like there is going to be a several pass compiler for this to
be a real deal here.

## Why create this?
I have a new database at Netflix with +100 unique events without definitions.
I will define them...

Here is a reason for why you could use it:

1. You have too many JSON objects to develop types for other than naming.
1. You may have enums that need to get pulled out.
1. You want as compact possible representation

## How To Use

1. clone
```
git clone git@github.com:ThePrimeagen/undefined.git
```

1. dependency installation
```
yarn install
```

1. have a file filled with json responses (check out `out`)

1. The data can be handed in a few ways
```
cat <jsons_here> | npx ts-node src/undefined.ts stdin
npx ts-node src/undefined.ts <json_here>
```

1. you want to save this to a file?
```
npx ts-node src/undefined.ts <json_here> > types.d.ts
```

## Enums
You can specify what fields need to be lifted into enums. I make the assumption
that enums are likely string values (though there is a case for me to fix this,
PRs will be merged with little regard)

```
npx ts-node src/undefined.ts <json_here> --enums Foo,Bar > types.d.ts
```

This will take any top level fields on objects and attempt to pull out the
values, convert it into an enum, put at top of definitions, and replace their
type (usually string) as the enum.

## There is an issue
Fix it and make a PR.  The code is shitty because i rage wrote it all in ~1
hour on twitch.

[ThePrimeagen](https://twitch.tv/ThePrimeagen)

## Support
Github sponsor or twitch prime babe!
