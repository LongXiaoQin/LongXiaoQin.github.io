---
title: Java_GUI
author: Jean
date: 2024-12-22
category: Develop
layout: post
mermaid: true
---



[参考链接1]: https://www.bilibili.com/video/BV1DJ411B75F/?spm_id_from=333.788.videopod.episodes&amp;vd_source=84070ec9f13d00198e3cfdd2cbad0c23&amp;p=3

[参考链接2]: https://mermaid.js.org/syntax/flowchart.html

# AWT

### 1.概述

```mermaid
flowchart LR
    component1["`Button
    TextArea
    Label
    ...`"]
    Component---->component1
    Component---->Container
    Container---->Window
    Container---->Panel
    Window---->Frame
    Window---->Dialog
    Panel---->Applet
    component1-.存在于容器中</br>add.->Container
```

### 2.组件与容器

#### Frame

```java
// 展示一个窗口
import java.awt.*;

public class TestFrame {
    public static void main(String[] args) {
        Frame frame = new Frame();
        frame.setBackground(Color.black);
        frame.setSize(200, 200);
        frame.setTitle("my first frame");
        frame.setLocation(100, 100);
        frame.setVisible(true);
    }
}
```

```java
// 展示多个窗口
import java.awt.*;

public class TestFrame2 {
    public static void main(String[] args) {
        MyFrame myFrame1 = new MyFrame(100, 100, 100, 100, Color.black);
        MyFrame myFrame2 = new MyFrame(200, 100, 100, 100, Color.green);
        MyFrame myFrame3 = new MyFrame(100, 200, 100, 100, Color.gray);
        MyFrame myFrame4 = new MyFrame(200, 200, 100, 100, Color.red);
    }
}

class MyFrame extends Frame{
    static int i = 0;
    MyFrame(int x, int y, int w, int h, Color color){
        super("my frame "+ (++i));
        setBackground(color);
        setSize(w, h);
        setLocation(x, y);
        setVisible(true);
    }
}
```

#### Panel

```java
// 画一个panel
import java.awt.*;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;

public class TestPanel {
    public static void main(String[] args) {
        Frame frame = new Frame();
        frame.setLayout(null);
        frame.setBounds(200, 200, 500, 500);
        frame.setBackground(new Color(0xB4B44A));
        Panel panel = new Panel();
        panel.setBackground(new Color(0x80B754));
        panel.setBounds(100, 100, 300, 300);
        frame.add(panel);
        frame.setVisible(true);
        frame.addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });
    }
}
```

### 3.布局管理

#### 流式布局

```java
import java.awt.*;

public class TestFlowLayout {
    public static void main(String[] args) {
        Frame frame = new Frame("TestFlowLayout");

        Button button1 = new Button("button1");
        Button button2 = new Button("button2");
        Button button3 = new Button("button3");

//        frame.setLayout(new FlowLayout());
//        frame.setLayout(new FlowLayout(FlowLayout.LEFT));
        frame.setLayout(new FlowLayout(FlowLayout.RIGHT));
        frame.setSize(500, 500);
        frame.add(button1);
        frame.add(button2);
        frame.add(button3);
        frame.setVisible(true);
    }
}
```

#### 东西南北中

```java
import java.awt.*;

public class TestBorderLayout {
    public static void main(String[] args) {
        Frame frame = new Frame();

        Button east = new Button("East");
        Button west = new Button("West");
        Button north = new Button("North");
        Button south= new Button("South");
        Button center = new Button("Center");

        frame.add(east, BorderLayout.EAST);
        frame.add(west, BorderLayout.WEST);
        frame.add(north, BorderLayout.NORTH);
        frame.add(south, BorderLayout.SOUTH);
        frame.add(center, BorderLayout.CENTER);

        frame.setBounds(500, 500, 200, 200);
        frame.setVisible(true);
    }
}
```

#### 表格布局

```java
import java.awt.*;

public class TestGridLayout {
    public static void main(String[] args) {
        Frame frame = new Frame();

        Button btn1 = new Button("btn1");
        Button btn2 = new Button("btn2");
        Button btn3 = new Button("btn3");
        Button btn4 = new Button("btn4");
        Button btn5 = new Button("btn5");
        Button btn6 = new Button("btn6");

        frame.setLayout(new GridLayout(3, 2));

        frame.add(btn1);
        frame.add(btn2);
        frame.add(btn3);
        frame.add(btn4);
        frame.add(btn5);
        frame.add(btn6);

        frame.pack();
        frame.setVisible(true);
    }
}
```

#### 综合应用

![image-20241222172330871](https://longxiaoqin.github.io/blog/pages/Develop/Java_GUI.assets/image-20241222172330871.png)

```java
import java.awt.*;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;

public class TestExercise {
    public static void main(String[] args) {
        Frame frame = new Frame();
        frame.setSize(400, 300);
        frame.setLocation(300, 400);
        frame.setBackground(Color.black);
        frame.setVisible(true);
        frame.setLayout(new GridLayout(2, 1));

        Panel p1 = new Panel(new BorderLayout());
        Panel p2 = new Panel(new GridLayout(2, 1));
        Panel p3 = new Panel(new BorderLayout());
        Panel p4 = new Panel(new GridLayout(2,2));

        // Top
        p1.add(new Button("East-1"), BorderLayout.EAST);
        p2.add(new Button("p2-btn1"));
        p2.add(new Button("p2-btn2"));
        p1.add(p2, BorderLayout.CENTER);
        p1.add(new Button("West-1"), BorderLayout.WEST);

        //Bottom
        p3.add(new Button("East-2"), BorderLayout.EAST);
        for(int i=1; i <= 4; i++){
            p4.add(new Button("p4-btn"+i));
        }
        p3.add(p4, BorderLayout.CENTER);
        p3.add(new Button("West-2"), BorderLayout.WEST);

        frame.add(p1);
        frame.add(p3);

        frame.addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });
    }
}
```

总结：

1.Frame是一个顶级窗口

2.Panel无法单独显示，需要添加到某个容器中

### 4.事件监听
