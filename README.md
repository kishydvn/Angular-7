# Angular-7
https://blog.angularindepth.com/creating-a-library-in-angular-6-

87799552e7e5
https://blog.angularindepth.com/creating-a-library-in-angular-6-

part-2-6e2bc1e14121

ng new your_project_name --createApplication=false
ng new angular7-series --createApplication=false
ng g application home --prefix=home --routing=true --style=scss

Before you serve home application make sure you run
npm install

Now you can serve this home application in development mode by 

executing following command
ng serve home -o --port 3000

You can create production build with this command
ng build home --prod

You can serve production build using http-server to replicate 

production app locally.
npm install http-server -g
http-server -p 8000 -c-1 dist/home


ng generate library ct-ng7-lib --prefix=cnl

ng build ct-ng7-lib

ng build ct-ng7-lib --watch

ng generate component libsample --project=ct-ng7-lib 

ct-ng7-lib.module.ts
import { LibsampleComponent } from './libsample/libsample.component';
exports: [CtNg7LibComponent, LibsampleComponent]

public_api.ts
export * from './lib/libsample/libsample.component';

FOR COMPONENTS:
Using export makes the element visible.
Adding it to the entry file makes the class visible

package.json to add a build_lib script:

"scripts": {
  ...
  "build_lib": "ng build ct-ng7-lib",
  ...
},

To build our library we can now use: npm run build_lib

After building our library we can build our application using:
ng build
This creates an example-ng6-lib-app directory in our workspace’s dist directory.

REMEMBER: Never directly modify the library distribution package.json.

Looking at our root package.json the relevant scripts look like this:

"scripts": {
  ...
  "build_lib": "ng build example-ng6-lib",
  "npm_pack": "cd dist/example-ng6-lib && npm pack",
  "package": "npm run build_lib && npm run npm_pack"
},

ALWAYS: Use npm pack to create the tgz file.

npm run package
