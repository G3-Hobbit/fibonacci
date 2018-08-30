# フィボナッチ数列の計算

## 今回覚えたtips

### 処理時間の計測

```sh
$ time node app.js

...
処理結果出力
...

real    0m1.095s
user    0m0.233s
sys     0m0.068s
```

### プロファイルツールを使う

```sh
$ node --prof app.js

...
処理結果出力
...

$ ls
README.md  app.js  isolate-0x2fbfe20-v8.log

$ node --prof-process isolate-0x2fbfe20-v8.log > out.log
$ less out.log

...
 [Summary]:
   ticks  total  nonlib   name
      9    0.8%    0.8%  JavaScript
   1110   98.6%   99.1%  C++
     13    1.2%    1.2%  GC
      6    0.5%          Shared libraries
      1    0.1%          Unaccounted
...

 [Bottom up (heavy) profile]:
  Note: percentage shows a share of a particular caller in the total
  amount of its parent calls.
  Callers occupying less than 1.0% are not shown.

   ticks parent  name
    473   42.0%  __write
    108   22.8%    v8::internal::Runtime_InterpreterDeserializeLazy(int, v8::internal::Object**, v8::internal::Isolate*)
     15   13.9%      Script: ~<anonymous> buffer.js:1:11
     15  100.0%        LazyCompile: ~NativeModule.compile internal/bootstrap/loaders.js:234:44
     15  100.0%          LazyCompile: ~NativeModule.require internal/bootstrap/loaders.js:138:34
...
```

[Summary] に、処理全体の概要が表示される

[Bottom up (heavy) profile] に、時間のかかった処理が表示される


