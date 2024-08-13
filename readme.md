
# how to build / deploy

you need to first install packages:

```sh
npm i
```

then build:

```sh
npm run build
```

zip it up:

```sh
cd _site
zip -r ../site.zip _site
```

> you do not want `_site/` as the
> root of the zip file

and then go to `AWS Amplify` (in the right region - us east 1),
click on the app `kewp.dev`, go to updates, select the zip file ...
and click Deploy ...

## new build

i've created a file `build.sh` that just runs `npm i` and `npm run build` ...

and now `package.json` is changed / the `build` script is changed,
so that `site.zip` is created properly ...