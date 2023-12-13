# 阿里云OSS存储桶操作指南
## 创建和配置存储桶
### 步骤1：登录阿里云控制台
首先，登录[阿里云控制台](https://www.aliyun.com/)。

### 步骤2：创建存储桶 
1. 在控制台中，选择“对象存储OSS”。
2. 点击“创建存储桶”按钮。
3. 填写存储桶名称，选择所在区域

### 步骤3：配置存储桶
1. 设置存储类型：根据需求选择标准存储、低频访问存储或归档存储。
2. 访问权限设置：选择公共读、公共读写或私有。
3. 高级设置：根据需要配置版本控制、日志记录等。

### 配置选项解释
- 存储类型：标准存储适用于频繁访问的数据；低频访问和归档存储适用于不常访问的数据。
- 访问权限：私有是最安全的选项，只有授权用户可以访问。
- 数据冗余：开启数据冗余可以进一步保证数据的安全性。

## 上传和管理大文件
### 使用OSS管理控制台
1. 进入创建的存储桶。
2. 点击“上传文件”按钮。
3. 选择需要上传的大文件并上传。

### 使用前端SDK
阿里云OSS提供了JavaScript SDK，方便前端直接上传文件到OSS。
```javascript
// 示例：使用ali-oss SDK上传文件
const OSS = require('ali-oss');

let client = new OSS({
  region: '<oss-region>',
  accessKeyId: '<Your AccessKeyId>',
  accessKeySecret: '<Your AccessKeySecret>',
  bucket: '<Your bucket name>'
});

async function put() {
  try {
    let result = await client.put('object-name', 'local-file');
    console.log(result);
  } catch (e) {
    console.error(e);
  }
}

put();
```
### 管理技巧
- 断点续传：对于特别大的文件，使用断点续传功能，提高上传的稳定性。
- 分片上传：将大文件分成多个小片，分别上传，然后在OSS上合并。
