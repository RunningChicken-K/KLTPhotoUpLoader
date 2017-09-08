# KLTPhotoKit
### 简化图片处理和上传


KLTPhotoKit实现了从图片的单选/多选到图片的单图/多图上传，并提供了附带上传进度显示的傻瓜式一键上传。
经过多次测试，无任何内存泄漏问题。


#### 如何安装
将工程文件夹中的PhotoKit文件夹拖入工程即可




##### 如何使用
导入`KLTPhotoKit.h`文件即可使用以下方法。


> **特别注意**：
> `uploadSingleImageWithUrl: FileName: Prarmeters: Completion:`是UIImageView的Category。

```
/**
 选取单张照片

 @param photoSource 图片来源 来自相册还是相机或全部   如果参数为全部 会弹出Alert
 @param title 弹出的alert的title
 @param msg 弹出的alert的message
 @param edited 是否允许编辑
 @param scaleSize 目标剪裁尺寸 如果不希望裁剪请传CGSizeZero
 @param compressRate 压缩比率区间 (0，1]  如果不希望有任何压缩 请传 0
 @param completion 选取完成后的回调
 */
+ (void)singlePhotoWithSource:(PhotoSource)photoSource alertTitle:(NSString *)title alertMessage:(NSString *)msg AllEdit:(BOOL)edited ScaleSize:(CGSize)scaleSize CompressRate:(CGFloat)compressRate Completion:(void (^)(UIImage * image))completion;



/**
 选取多张照片

 @param size 目标尺寸 返回图片大小的估值 返回的图片的实际尺寸会以此值作为参考  且不影响图片实际比例
 @param limitCount 图片的最大选取数量
 @param completion 成功获取到图片后的回调
 */
+ (void)multiPhotosWithTargetSize:(CGSize)size LimitCount:(NSInteger)limitCount Completion:(void (^)(NSArray * imagesArray))completion;




/**
 上传多张图片

 @param images images是一个字典 其中的每一对Key-Value key是要给服务器的图片/文件名  value为图片/文件本身
 @param url 目标服务器地址
 @param parameters 二进制参数
 @param progress 上传进度
 @param completion 上传结束后的回调
 */
+ (void)uploadImages:(NSDictionary *)images Url:(NSString *)url Parameters:(NSDictionary *)parameters Progress:(void (^)(CGFloat progress))progress Completion:(void(^)(NSData * data,NSError * error))completion;

/**
UIImageView的Category
 获取单张图片并把相应参数和图片上传到指定URL
 */
-  (KLTImageUPLoader *)uploadSingleImageWithUrl:(NSString *)url FileName:(NSString *)fileName Prarmeters:(NSDictionary *)parameters Completion:(void (^)(NSData * data,UIImageView * imageView))completion;```


