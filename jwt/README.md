# jwt

## Who

```
github.com/pascaldekloe/jwt v1.9.0
vs
github.com/cristalhq/jwt/v3 v3.0.1
```

## Where

```
MacBook Pro (15-inch, 2017)
2,8 GHz Quad-Core Intel Core i7
16 GB 2133 MHz LPDDR3
```

## How

```shell script
# make benchmarks as an executable
$ go test -c -o jwt-bench

# run them
$ time ./jwt-bench -test.v -test.benchmem -test.bench ^Benchmark -test.count 10 -test.run ^$ > bench.txt

# split output into files
$ sed 's/_One_//' bench.txt > one.txt
$ sed 's/_Two_//' bench.txt > two.txt

# final results
$ benchstat one.txt two.txt > result.txt
```

## Well

```
name                      old time/op    new time/op    delta
ECDSA/sign-ES256-4          27.2µs ± 1%    27.6µs ± 0%    +1.39%  (p=0.000 n=10+10)
ECDSA/sign-ES384-4          4.35ms ± 0%    4.36ms ± 0%    +0.39%  (p=0.001 n=10+9)
ECDSA/sign-ES512-4          7.53ms ± 0%    7.57ms ± 1%    +0.54%  (p=0.004 n=9+9)
ECDSA/check-ES512-4         15.2ms ± 0%    14.6ms ± 0%    -3.76%  (p=0.000 n=9+9)
EdDSA/sign-EdDSA-4          51.5µs ± 0%    52.2µs ± 0%    +1.22%  (p=0.000 n=10+10)
EdDSA/check-EdDSA-4          136µs ± 1%     137µs ± 0%    +0.76%  (p=0.000 n=10+10)
HMAC/sign-HS256-4           2.08µs ± 0%    3.22µs ± 0%   +54.66%  (p=0.000 n=10+9)
HMAC/sign-HS256-reuse-4     1.69µs ± 1%    1.90µs ± 1%   +12.43%  (p=0.000 n=9+10)
HMAC/check-HS256-4          4.18µs ± 0%    5.21µs ± 0%   +24.58%  (p=0.000 n=10+10)
HMAC/check-HS256-reuse-4    3.86µs ± 0%    3.98µs ± 1%    +3.15%  (p=0.000 n=10+10)
HMAC/sign-HS384-4           2.37µs ± 1%    3.54µs ± 0%   +49.36%  (p=0.000 n=10+8)
HMAC/sign-HS384-reuse-4     1.83µs ± 1%    2.06µs ± 1%   +12.36%  (p=0.000 n=10+10)
HMAC/check-HS384-4          4.48µs ± 0%    5.63µs ± 0%   +25.67%  (p=0.000 n=9+10)
HMAC/check-HS384-reuse-4    4.02µs ± 0%    4.13µs ± 1%    +2.52%  (p=0.000 n=10+9)
HMAC/sign-HS512-4           2.41µs ± 1%    3.58µs ± 0%   +48.84%  (p=0.000 n=10+10)
HMAC/sign-HS512-reuse-4     1.87µs ± 1%    2.10µs ± 1%   +12.24%  (p=0.000 n=10+10)
HMAC/check-HS512-4          4.55µs ± 0%    5.68µs ± 0%   +24.77%  (p=0.000 n=10+9)
HMAC/check-HS512-reuse-4    4.08µs ± 1%    4.21µs ± 1%    +3.33%  (p=0.000 n=10+9)
RSA/sign-1024-bit-4          328µs ± 1%     328µs ± 0%      ~     (p=0.931 n=9+9)
RSA/sign-2048-bit-4         1.49ms ± 0%    1.49ms ± 1%    +0.28%  (p=0.029 n=10+10)
RSA/sign-4096-bit-4         8.11ms ± 1%    8.06ms ± 0%    -0.62%  (p=0.001 n=10+8)

name                      old alloc/op   new alloc/op   delta
ECDSA/sign-ES256-4          3.04kB ± 0%    3.38kB ± 0%   +11.05%  (p=0.000 n=10+10)
ECDSA/sign-ES384-4          1.75MB ± 0%    1.75MB ± 0%      ~     (p=0.853 n=10+10)
ECDSA/sign-ES512-4          3.02MB ± 0%    3.03MB ± 0%      ~     (p=0.105 n=10+10)
ECDSA/check-ES512-4         6.25MB ± 0%    5.96MB ± 0%    -4.66%  (p=0.000 n=10+10)
EdDSA/sign-EdDSA-4            672B ± 0%      912B ± 0%   +35.71%  (p=0.000 n=10+10)
EdDSA/check-EdDSA-4         1.66kB ± 0%    1.59kB ± 0%    -4.33%  (p=0.000 n=10+10)
HMAC/sign-HS256-4             656B ± 0%     1726B ± 0%  +163.11%  (p=0.000 n=10+10)
HMAC/sign-HS256-reuse-4       176B ± 0%      400B ± 0%  +127.27%  (p=0.000 n=10+10)
HMAC/check-HS256-4          1.81kB ± 0%    2.48kB ± 0%   +37.22%  (p=0.000 n=10+9)
HMAC/check-HS256-reuse-4    1.33kB ± 0%    1.30kB ± 0%    -1.81%  (p=0.000 n=10+10)
HMAC/sign-HS384-4           1.01kB ± 0%    2.07kB ± 0%  +105.65%  (p=0.000 n=10+9)
HMAC/sign-HS384-reuse-4       208B ± 0%      432B ± 0%  +107.69%  (p=0.000 n=10+10)
HMAC/check-HS384-4          2.24kB ± 0%    2.83kB ± 0%   +26.16%  (p=0.000 n=10+10)
HMAC/check-HS384-reuse-4    1.44kB ± 0%    1.34kB ± 0%    -7.22%  (p=0.000 n=10+10)
HMAC/sign-HS512-4           1.02kB ± 0%    2.11kB ± 0%  +105.66%  (p=0.000 n=10+10)
HMAC/sign-HS512-reuse-4       224B ± 0%      464B ± 0%  +107.14%  (p=0.000 n=10+10)
HMAC/check-HS512-4          2.27kB ± 0%    2.86kB ± 0%   +25.79%  (p=0.000 n=10+10)
HMAC/check-HS512-reuse-4    1.47kB ± 0%    1.37kB ± 0%    -7.07%  (p=0.000 n=10+10)
RSA/sign-1024-bit-4         16.7kB ± 0%    16.9kB ± 0%    +1.54%  (p=0.000 n=10+10)
RSA/sign-2048-bit-4         31.4kB ± 0%    31.6kB ± 0%    +0.72%  (p=0.000 n=10+10)
RSA/sign-4096-bit-4         77.6kB ± 0%    77.9kB ± 0%    +0.46%  (p=0.000 n=9+9)

name                      old allocs/op  new allocs/op  delta
ECDSA/sign-ES256-4            35.0 ± 0%      42.0 ± 0%   +20.00%  (p=0.000 n=10+10)
ECDSA/sign-ES384-4           14.4k ± 0%     14.4k ± 0%      ~     (p=0.839 n=10+10)
ECDSA/sign-ES512-4           19.6k ± 0%     19.6k ± 0%    +0.15%  (p=0.050 n=10+10)
ECDSA/check-ES512-4          40.4k ± 0%     38.6k ± 0%    -4.50%  (p=0.000 n=10+10)
EdDSA/sign-EdDSA-4            7.00 ± 0%     11.00 ± 0%   +57.14%  (p=0.000 n=10+10)
EdDSA/check-EdDSA-4           28.0 ± 0%      27.0 ± 0%    -3.57%  (p=0.000 n=10+10)
HMAC/sign-HS256-4             7.00 ± 0%     17.00 ± 0%  +142.86%  (p=0.000 n=10+10)
HMAC/sign-HS256-reuse-4       2.00 ± 0%      6.00 ± 0%  +200.00%  (p=0.000 n=10+10)
HMAC/check-HS256-4            31.0 ± 0%      35.0 ± 0%   +12.90%  (p=0.000 n=10+10)
HMAC/check-HS256-reuse-4      26.0 ± 0%      26.0 ± 0%      ~     (all equal)
HMAC/sign-HS384-4             7.00 ± 0%     17.00 ± 0%  +142.86%  (p=0.000 n=10+10)
HMAC/sign-HS384-reuse-4       2.00 ± 0%      6.00 ± 0%  +200.00%  (p=0.000 n=10+10)
HMAC/check-HS384-4            32.0 ± 0%      35.0 ± 0%    +9.38%  (p=0.000 n=10+10)
HMAC/check-HS384-reuse-4      27.0 ± 0%      26.0 ± 0%    -3.70%  (p=0.000 n=10+10)
HMAC/sign-HS512-4             7.00 ± 0%     17.00 ± 0%  +142.86%  (p=0.000 n=10+10)
HMAC/sign-HS512-reuse-4       2.00 ± 0%      6.00 ± 0%  +200.00%  (p=0.000 n=10+10)
HMAC/check-HS512-4            32.0 ± 0%      35.0 ± 0%    +9.38%  (p=0.000 n=10+10)
HMAC/check-HS512-reuse-4      27.0 ± 0%      26.0 ± 0%    -3.70%  (p=0.000 n=10+10)
RSA/sign-1024-bit-4            106 ± 0%       110 ± 0%    +3.77%  (p=0.000 n=10+10)
RSA/sign-2048-bit-4            112 ± 0%       116 ± 0%    +3.57%  (p=0.000 n=10+10)
RSA/sign-4096-bit-4            126 ± 0%       130 ± 0%    +3.17%  (p=0.000 n=10+9)
```
