
##### 设计4个线程，其中两个每次对j增加1，另外两个对j每次减少1，循环100次。

```
package com.wangli.thread;

public class Thread2 implements Runnable {
    private Test test;

    public Thread2(Test test) {
        this.test = test;
    }

    @Override
    public void run() {
        for (int i=0;i<100;i++) {
            test.add();
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}

```

```
package com.wangli.thread;

public class Thread3 implements Runnable {
    private Test test;

    public Thread3(Test test) {
        this.test = test;
    }

    @Override
    public void run() {
        for (int i=0;i<100;i++) {
            test.minus();
            try {
                Thread.sleep(2000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}

```
package com.wangli.thread;

public class Test {
    private int j;

    public synchronized void add() {
        j++;
        System.out.println(Thread.currentThread().getName() + ":add - " + j);
    }

    public synchronized void minus() {
        j--;
        System.out.println(Thread.currentThread().getName() + ":minus - " + j);
    }

    public static void main(String[] args) {
        Test t = new Test();
        for (int i=0;i<2;i++) {
            Thread t1 = new Thread(new Thread2(t));
            t1.start();
            Thread t2 = new Thread(new Thread3(t));
            t2.start();
        }
    }
}

```

```
