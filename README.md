# HomeWork4
## 自定义webview代码
```
      protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);
        webView=findViewById(R.id.web1);
        String url=getIntent().getExtras().getString("url");
        webView.loadUrl(url);
    }
```
## intent网址跳转代码
```
bt1.setOnClickListener(new View.OnClickListener(){
            @Override
            public void onClick(View view){
                Intent in1= new Intent(Intent.ACTION_VIEW);
                EditText ed =findViewById(R.id.editText);
                final String net= ed.getText().toString();
                if (isValidUrl(net)){
                    in1.setData(Uri.parse(net));
                }
                else{
                    Toast.makeText(MainActivity.this,"请输入正确网址",Toast.LENGTH_SHORT).show();
                }
                startActivity(in1);
            }
        });
```    
## 验证url是否合法代码
```
      public static boolean isValidUrl(String urlString){
        URI uri = null;
        try {
            uri = new URI(urlString);
        } catch (URISyntaxException e) {
            e.printStackTrace();
            return false;
        }

        if(uri.getHost() == null){
            return false;
        }
        if(uri.getScheme().equalsIgnoreCase("http") || uri.getScheme().equalsIgnoreCase("https")){
            return true;
        }
        return false;
    }
```
## 截图
![截图](https://github.com/ankleing/HomeWork4/tree/main/image/image1.png)
