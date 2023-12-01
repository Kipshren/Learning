![[Pasted image 20230930174627.png|800]]



窗口必须是Frame创建的
再将Component的中的组件放到窗口中
Container将各个组件包装起来

CheckBoxGroup直接继承于Object类，跟Component是一层级别，作用类似于Container将CheckBox按钮包在一起。但把checkbox放group里面只能用checkbox的构造器，cbg没有增加方法

box是swing新出来的一个容器，他的构造对象方法不是new而是create方法

Dialog
模式对话框---创造出后不能操作父窗口，必须把模式对话框关闭才能操作父窗口
非模式对话框---创造出后任意操作父窗口
FileDialog
对话框的选择由运行的系统(平台)决定，Win是模式对话框

事件监听器
只用把Listener记住，然后ctrl+点击直接看源码实现什么抽象方法
![[Pasted image 20230930201851.png]]

监听器有两种构造方法
1、直接addxxxListener，在方法头执行接口方法
2、构造xxxListener内部类实现接口，创造监听器对象

```java
//1、方法一
tf.addTextListener(new TextListener(){
	@Override  
	public void textValueChanged(TextEvent e) {  
	String tx = tf.getText();  
	System.out.println("输出: "+tx);  
}
});

//2、方法二
txListener txl = new txListener();//方法三就是在这;前面加{}接口方法
tf.addTextListener(txl);

private void txListener() implements TextListener{
	@Override  
	public void textValueChanged(TextEvent e) {  
	String tx = tf.getText();  
	System.out.println("输出: "+tx);  
}
```


菜单
![[Pasted image 20230930212601.png]]

![[Pasted image 20230930212515.png|600]]


awt总体：
创建各个小组件
init()组装---->从局部->大体
main调用init()

自定义的画布类是内部类定义的
绘制和画面更新都是调用画布对象的paint()方法和repaint()方法

fillrect()的绘图坐标都是在左上角



![[Pasted image 20231006223429.png]]
























