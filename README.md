# RxBus2
Rxbus2 by rxjava2.0

#### used
Gradle 
```
compile 'lib.gorden.rxbus2:rxbus:2.0.1'
```

Maven
```
<dependency>
  <groupId>lib.gorden.rxbus2</groupId>
  <artifactId>rxbus</artifactId>
  <version>2.0.1</version>
  <type>pom</type>
</dependency>
```
####使用介绍
```
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        RxBus.get().register(this);
    }


    public void test1005(View view){
        RxBus.get().send(1005);
    }
    public void test1005String(View view){
        RxBus.get().send(1005,"字符串数据");
    }
    public void test1005Int(View view){
        RxBus.get().send(1005,1303);
    }
    public void test1005Object(View view){
        RxBus.get().send(1005,new ArrayList<String>());
    }

    public void test1007(View view){
        RxBus.get().send(1007);
    }
    public void test1007String(View view){
        RxBus.get().send(1007,"字符串数据");
    }
    public void test1007Int(View view){
        RxBus.get().send(1007,1303);
    }
    public void test1007Object(View view){
        RxBus.get().send(1007, new ArrayList<String>());
    }


    @Subscribe(code = 1005,
            threadMode = ThreadMode.MAIN)
    public void receive1005(){
        Log.i("rxbus_log","code  1005 ");
    }

    @Subscribe(code = 1005,
    threadMode = ThreadMode.CURRENT_THREAD)
    public void receive1005(String msg){
        Log.i("rxbus_log","code  1005  String:"+msg);
    }
    @Subscribe(code = 1005)
    public void receive1005(Integer msg){
        Log.i("rxbus_log","code  1005  int:"+msg);
    }
    @Subscribe(code = 1005)
    public void receive1005(ArrayList msg){
        Log.i("rxbus_log","code  1005  data:"+msg);
    }

    @Subscribe(code = 1007)
    public void receive1007(){
        Log.i("rxbus_log","code  1007 ");
    }

    @Subscribe(code = 1007)
    public void receive1007(String msg){
        Log.i("rxbus_log","code  1007  String:"+msg);
    }
    @Subscribe(code = 1007)
    public void receive1007(Integer msg){
        Log.i("rxbus_log","code  1007  int:"+msg);
    }
    @Subscribe(code = 1007)
    public void receive1007(ArrayList msg){
        Log.i("rxbus_log","code  1007  data:"+msg);
    }


    @Override
    protected void onDestroy() {
        super.onDestroy();
        RxBus.get().unRegister(this);
    }
}
```
