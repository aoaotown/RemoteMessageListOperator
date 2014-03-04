# RemoteMessageListOperator

![Mou icon](http://kidswant.u.qiniudn.com/FoP984K9vvB88dIW7UDZqRazVV5s)  

## Requirements

**tinkl**, is some of my experiences,hope that can help *ios  developers*.

**RemoteMessageListOperator** uses ARC and requires iOS 7.0+.

It probably will work with iOS 6, I have not tried,but  it is not using any iOS7 specific APIs.
 
####  Installation

> just download zip file… &gt; and you can use it .

#### Links and Email

if you have some Question to ask me, you can contact email <nicolastinkl@gmail.com> link.

or see blogs <http://www.cnblogs.com/tinkl/p/3573454.html>

[id]: http://mouapp.com "Markdown editor on Mac OS X"



#### Some Code

Just see this:



- (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath

-	 [cell SendMessageRemoteImgOper:_objImgListOper WithMessage:dictionary type:messageType_text];


#### Execution
 

```
- (void) SendMessageRemoteImgOper:(RemoteImgListOperator *)objOper WithMessage:(NSMutableDictionary *) dict type:(int) type
{

    NSString * guid =  dict[@"MESSAGE_GUID"];
    [self setRemoteImgOper:objOper withGUID:guid];
    SLLog(@"SendMessageRemoteImgOper guid : %@",guid);
    __block NSMutableDictionary *blockDict = [dict mutableCopy];
    dispatch_async(dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0), ^{
        dispatch_sync(dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0), ^{
            dispatch_async(dispatch_get_main_queue(), ^{
                if (_objRemoteImgListOper)
                {
                    [_objRemoteImgListOper sendMessageGUID:guid ByDict:blockDict withProgress:nil];
                }
            });
        });
    });
}

```



####  Features

------------------------------------

1. Gives Xcode's autocompletion to be able to filter like Open Quickly does2. Ordered  
3. Supports Xcode 5.0, 5.0.1, 5.0.2 and 5.1
4. Supports Xcode's learning and context-aware priority system
5. Uses Grand Central Dispatch to parallelise matching
6. Productivity++ 

#### Notes

--------

* Only tested with Xcode 5 on 10.8.5
* Hasn't been tested with other plugins 



#### Changelog

Setext-style:


1.0 - 2014/02/04
----------

Initial release
