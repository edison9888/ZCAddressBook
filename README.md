ZCAddressBook
=============

封装通讯录、短信功能
//版本说明 iOS研究院 305044955
/*
 2014.4 18
 1.2版本 ZC封装的自定义通讯录界面
 1、解决了iOS7下无数据的问题，增加判断版本
 2、更正类名 由原来的CustomAddressBook修改为ZCAddressBook
 3、增加了发送短信功能
 2014.4.8
 1.1版本 获得的数据进行排序的函数
 解决了中文拼音的问题，处理英文拼写的问题
 2014.4.7
 1.0版本 ZC封装的自定义通讯录界面
 */
/*
 代码示例
 1、使用本类需要加入MessageUI~AddressBookUI~AddressBook3个系统库
 2、还需要有pingyin文件
 3、发送短信需要使用真机才可以
 
 //添加联系人 label是备注
 BOOL isSucceed=[[ZCAddressBook shareControl]addContactName:@"张三" phoneNum:@"34456789"withLabel:@"dfghjklvbn"];
 //获得Vcard
 NSMutableDictionary*dic= [[ZCAddressBook shareControl]getPersonInfo];
 //获得序列索引
 NSArray*array=[[ZCAddressBook shareControl]sortMethod];
 
 //发送短信,群发，可以有指定内容
 [[ZCAddressBook alloc]initWithTarget:self MessageNameArray:@[@"13811928431"] Message:@"发送消息的内容" Block:^(int type) {
 NSLog(@"发送短信后的状态");
 }];
 //调用系统控件，选中后获得指定人信息
 [[ZCAddressBook alloc]initWithTarget:self PhoneView:^(BOOL isSucceed, NSDictionary *dic) {
 NSLog(@"从系统中获得指定联系人的信息%@",dic);
 }];
 
 //跳出程序进行发送短信
 [ZCAddressBook sendMessage:@"13811928431"];
 */

/*
 方法说明
 多少段以及相应顺序 sortMethod 返回的数据
 构建界面，数据使用 getPersonInfo 返回的数据，key通过sortMethod获得
 //key是A-Z的标记   每个value是数组，每个数组成员是字典，每个字典记录每个联系人的具体内容
 //字典是无序的需要对allkeys进行排序
 -(NSMutableDictionary*)getPersonInfo;
 
 //获得排序后的序列
 -(NSArray*)sortMethod;
 
 // 查询指定号码是否已存在于通讯录
 // 返回值：
 //　　ABHelperCanNotConncetToAddressBook -> 连接通讯录失败（iOS6之后访问通讯录需要用户许可）
 //　　ABHelperExistSpecificContact　　　　-> 号码已存在
 //　　ABHelperNotExistSpecificContact　　-> 号码不存在
 // 添加联系人（联系人名称、号码、号码备注标签）
 
 */
