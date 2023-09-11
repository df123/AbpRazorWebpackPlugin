# AbpRazorWebpackPlugin
添加abp-script到ASP.NET Core Razore页面 

# 用法
复制文件到项目目录，然后在webpack.config.js中引入
 ```
const AbpRazorWebpackPlugin = require('./plugin/AbpRazorWebpackPlugin/index.js')
module.exports = {
    entry: {
        Test1: './src/Test1/main.ts',
        Test2: './src/Test2/main.ts'
    },
    output: {
        filename: '[name].entry.js',
        path: path.resolve(__dirname, '..', 'wwwroot', 'dist')
    },
    plugins: [
        new AbpRazorWebpackPlugin({ path: 'dist', htmlpath: '../Pages' })
    ]
};
```

需要参数path，和htmlpath
```
path:是webpack打包生成的目录
htmlpath：是Razor页面所在的目录
```

对于需要在webpack打包后自动导入abp-script，需要添加注释@* [entryname] *@(如下),位于注释中间的代码会别替换
```
@section scripts{
    @* Test1 *@
<abp-script src="/dist/Test1.entry.js"></abp-script>
    @* Test1 *@
}
```
