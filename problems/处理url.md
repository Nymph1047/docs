## 原先获取上传后的文件URL的方式
```vue
const fileUrl = client.generateObjectUrl(objectKey);
console.log('File URL:', fileUrl);
```
## 原因：私有Bucket：如果您的OSS Bucket设置为私有（默认设置），那么直接通过URL是无法访问文件的。您需要生成一个带签名的URL，才能访问这些私有文件

## 解决方法：在生成URL时使用带有有效期的签名。例如：
```vue
const fileUrl = client.signatureUrl(objectKey, { expires: 3600 });
console.log('Signed File URL:', fileUrl);
```
