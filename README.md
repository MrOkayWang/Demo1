# Demo1
练习activity的通信从A->B再返回并传递数据


 1、显式跳转和隐式跳转

AActivity -> BActivity
显式跳转：
 显式1种：Intent intent=new Intent(this,BActivity.class);
            startActivity(intent);
（intent在英文中为意图的意思）


显式2种：Intent intent=new Intent( ）;
                intent.setClass(this,BActivity.class);
                startActivity(intent);


显式3种: Intent intent=new Intent( );
                intent.setClassName(this,"包名地址")；                                                 // eg:"com.xxxx.xxx.xx.BActivity" 
                startActivity(intent);

  显式4种: Intent intent=new Intent( );          
                intent.setComponent(new ComponentName(this,"包名地址"))；
                startActivity(intent);
隐式跳转：

隐式1种： Intent intent=new Intent( );    
                intent.setAction("xxxxxxxxxx");
                startActivity(intent);
2、Activity之间的数据传递
  发送：   Intent intent=new Intent(this,BActivity.class);
                 Bundle bundle=new Bundle();
                 bundle.putString("name","字符串")；
                 bundle.putInt("number",123)  ;
                      intent.putExtras(Bundle)
                 startActivity(intent);
        

数据传递是通过Bundle

接收： Bundle bundle=getIntent( ).getExtras;
                    bundle.getString("name");
                    bundle.getInt("number");

3.StartActivityForResult

A->B, 从B回到A，并传给A一些信息


B:在 B中创建一个button  给button添加一个点击事件，返回A并且向A传递数据

在点击事件中这样写：
Intent intent=new Intent();
Bundle bundle=new Bundle;
bundle.putString("xxx","aaa");
intent.putExtras(bundle);
setResult(Activity.RESULT_OK,intent);
finish( );

A：A中用一个Toast来展示从B接受到的数据
首先A中不写 startActivity( )方法而是startActivityForResult( )
startActivityForResult( )
传入两个参数一是intent ,二是一个数字可以随便写用于区分
参数二 是requestCode
startActivityForResult(intent,0 );
然后重写onActivityResult
此方法有int requestCode, int resultCode, Intent data三个参数
int requestCode即startActivityForResult(intent,0 )中的0
int resultCode即B中setResult(Activity.RESULT_OK,intent)中的Activity.RESULT_OK
 最后
Toast.makeTest(AActivity.this,data.getExtras.getString("xxx"),Toast.LENGTH_LONG).show;


















               
 
        
        
