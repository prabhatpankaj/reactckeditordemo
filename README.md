# How to create a custom build of CKEditor 5

After implementing CKEditor into your app you will notice that it lacks a lot of basic funtions. There are even no alignment or font color options. So the basic build is not very useful at the moment. The only way to extend its capability is by adding new plugins. And the only way to add new plugins is to create a custom build. The process troubles a lot of developers.


* Forking the official repo

After cloning go to the root folder of the framework. It's time to separate your editor type from the rest of the framework. I chose classic one so I am going to separate ckeditor5-build-classic. In order to do that just change current directory to the chosen build.

```
git clone -b stable https://github.com/ckeditor/ckeditor5

```

Create copy of ckeditor5-build-classic as ckeditor5-build-classic-custom and rename "@ckeditor/ckeditor5-build-classic" to "@ckeditor/ckeditor5-build-classic" in package.json.

```

cp -r ckeditor5/packages/ckeditor5-build-classic ckeditor5-build-classic-custom

```

change current directory to the chosen build.

```
cd ckeditor5-build-classic-custom

```

* Adding plugins
 
For example if you want to implement the Alignment plugin you have to add three lines of code to the ckeditor.js file and install the plugin files through npm or yarn.

```
import Alignment from '@ckeditor/ckeditor5-alignment/src/alignment';
 

ClassicEditor.builtinPlugins = [
   Alignment,
   ... some other plugins
 

When adding a plugin to the toolbar stick with camel case format (i.e. for the fontcolor plugin it will be fontColor)

ClassicEditor.defaultConfig = {
toolbar: {
   items: [
      'alignment',
 

npm install @ckeditor/ckeditor5-alignment
 
```
You have to follow the above steps for any additonal plugin you are going to include in your build.

You can also make other changes. Maybe you want to delete some default package from your stating build or maybe you wan't to add some of your own plugin or programable button? If so you can do this before committing the changes.

When you finish install all dependencies from package.json.

```
npm install
```
 
* Testing the build
 

Time to create your build. The command below generates build folder with essentials files which are basically your whole customised editor.

```
npm run build

```

Install and configure generated build in project

 Copy the custom build files into your app (anywhere convenient for you but not into the node__modules folder!). Then use npm to install it in the node__modules by specifying the folder path.

```
cd ..

npm install ckeditor5-build-classic-custom/

``` 

Then once again install npm dependencies.

```
npm install
 
```

From now one you can import your custom build using the name from the local module registered in package.json.


