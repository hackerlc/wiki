### Rxjava
类似于观察者模式
#### 1
```
    Observable<String> mObservable = rx.Observable.create(new Observable.OnSubscribe<String>() {
        @Override
        public void call(Subscriber<? super String> subscriber) {
            subscriber.onNext("Hello world");
            subscriber.onCompleted();
        }
    });
    Subscriber<String> mSubscriber =new Subscriber<String>() {
        @Override
        public void onCompleted() {

        }

        @Override
        public void onError(Throwable e) {

        }

        @Override
        public void onNext(String s) {
            System.out.println(s);
        }
    };
    
    // 调用
    mObservable.subscribe(mSubscriber);
```

#### 2
```
        Observable.just("Hello world").subscribe(new Action1<String>() {
            @Override
            public void call(String s) {
                System.out.println(s);
            }
        });
```

### 3 Rxjava+Lambda
```
Observable.just("Hello world").subscribe(s -> System.out.println(s));
```
