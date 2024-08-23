## How to patch files

---

How would someone patch your files in your local node_modules folder? It is not
something that goes unto GitHub, so how do we share that patch?

For example, in my project ItemNook we needed Next.js to find a file in a 
different place for the pages. This helped with organization in the project.

## How to
1. Create a git diff of any changes you have made.

2. Apply the patch
```shell
git apply yourPatch.patch
```

3. Make command in package.json (optional)
```json
{
  "scripts": {
    "patch": "git apply yourPatch.patch"
  }
}
```