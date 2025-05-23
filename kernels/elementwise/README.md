# Elementwise

## 0x00 说明

包含以下内容：

- [X] elementwise_add_f32_kernel
- [X] elementwise_add_f32x4_kernel(float4向量化版本)
- [X] elementwise_add_f16_kernel(fp16版本)
- [X] elementwise_add_f16x2_kernel(fp16向量化版本)
- [X] elementwise_add_f16x8_kernel(fp16向量化版本)
- [X] elementwise_add_f16x8_pack_kernel(fp16向量化版本, pack)
- [X] PyTorch bindings


## 测试

```bash
# 只测试Ada架构 不指定默认编译所有架构 耗时较长: Volta, Ampere, Ada, Hopper, ...
export TORCH_CUDA_ARCH_LIST=Ada
python3 elementwise.py
```

输出:

```bash
-------------------------------------------------------------------------------------
                                        S=1024, K=1024
           out_f32: [-2.82009077, -0.5666312], time:0.00598025ms
         out_f32x4: [-2.82009077, -0.5666312], time:0.00410318ms
        out_f32_th: [-2.82009077, -0.5666312], time:0.00588393ms
-------------------------------------------------------------------------------------
           out_f16: [-2.8203125, -0.56640625], time:0.00548601ms
         out_f16x2: [-2.8203125, -0.56640625], time:0.00389791ms
         out_f16x8: [-2.8203125, -0.56640625], time:0.00386930ms
     out_f16x8pack: [-2.8203125, -0.56640625], time:0.00386310ms
        out_f16_th: [-2.8203125, -0.56640625], time:0.00583792ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=1024, K=2048
           out_f32: [4.86788559, -0.03121264], time:0.00742459ms
         out_f32x4: [4.86788559, -0.03121264], time:0.00618076ms
        out_f32_th: [4.86788559, -0.03121264], time:0.00621343ms
-------------------------------------------------------------------------------------
           out_f16: [4.8671875, -0.03118896], time:0.00691319ms
         out_f16x2: [4.8671875, -0.03118896], time:0.00612307ms
         out_f16x8: [4.8671875, -0.03118896], time:0.00572920ms
     out_f16x8pack: [4.8671875, -0.03118896], time:0.00393581ms
        out_f16_th: [4.8671875, -0.03118896], time:0.00588250ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=1024, K=4096
           out_f32: [-0.76231986, 0.14095858], time:0.01322269ms
         out_f32x4: [-0.76231986, 0.14095858], time:0.01232338ms
        out_f32_th: [-0.76231986, 0.14095858], time:0.01074243ms
-------------------------------------------------------------------------------------
           out_f16: [-0.76269531, 0.14099121], time:0.01203275ms
         out_f16x2: [-0.76269531, 0.14099121], time:0.01031137ms
         out_f16x8: [-0.76269531, 0.14099121], time:0.01143646ms
     out_f16x8pack: [-0.76269531, 0.14099121], time:0.00615382ms
        out_f16_th: [-0.76269531, 0.14099121], time:0.00615549ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=2048, K=1024
           out_f32: [1.7307409, -1.32978106], time:0.01031971ms
         out_f32x4: [1.7307409, -1.32978106], time:0.00623751ms
        out_f32_th: [1.7307409, -1.32978106], time:0.00620961ms
-------------------------------------------------------------------------------------
           out_f16: [1.73046875, -1.32910156], time:0.00949526ms
         out_f16x2: [1.73046875, -1.32910156], time:0.00459051ms
         out_f16x8: [1.73046875, -1.32910156], time:0.00563455ms
     out_f16x8pack: [1.73046875, -1.32910156], time:0.00408101ms
        out_f16_th: [1.73046875, -1.32910156], time:0.00587082ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=2048, K=2048
           out_f32: [0.39944169, 0.4179616], time:0.01319146ms
         out_f32x4: [0.39944169, 0.4179616], time:0.01057196ms
        out_f32_th: [0.39944169, 0.4179616], time:0.01073718ms
-------------------------------------------------------------------------------------
           out_f16: [0.3996582, 0.41845703], time:0.01202869ms
         out_f16x2: [0.3996582, 0.41845703], time:0.01047349ms
         out_f16x8: [0.3996582, 0.41845703], time:0.00978184ms
     out_f16x8pack: [0.3996582, 0.41845703], time:0.00608325ms
        out_f16_th: [0.3996582, 0.41845703], time:0.00611973ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=2048, K=4096
           out_f32: [-0.80888653, 1.04407156], time:0.05168271ms
         out_f32x4: [-0.80888653, 1.04407156], time:0.05156827ms
        out_f32_th: [-0.80888653, 1.04407156], time:0.05278206ms
-------------------------------------------------------------------------------------
           out_f16: [-0.80908203, 1.04394531], time:0.02227950ms
         out_f16x2: [-0.80908203, 1.04394531], time:0.01890278ms
         out_f16x8: [-0.80908203, 1.04394531], time:0.02116466ms
     out_f16x8pack: [-0.80908203, 1.04394531], time:0.01065993ms
        out_f16_th: [-0.80908203, 1.04394531], time:0.01049185ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=4096, K=1024
           out_f32: [-0.49592674, 0.89274263], time:0.01889443ms
         out_f32x4: [-0.49592674, 0.89274263], time:0.01069832ms
        out_f32_th: [-0.49592674, 0.89274263], time:0.01063895ms
-------------------------------------------------------------------------------------
           out_f16: [-0.49584961, 0.89257812], time:0.01725316ms
         out_f16x2: [-0.49584961, 0.89257812], time:0.00749230ms
         out_f16x8: [-0.49584961, 0.89257812], time:0.00951600ms
     out_f16x8pack: [-0.49584961, 0.89257812], time:0.00611234ms
        out_f16_th: [-0.49584961, 0.89257812], time:0.00612116ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=4096, K=2048
           out_f32: [-1.08919787, -1.8021946], time:0.03161430ms
         out_f32x4: [-1.08919787, -1.8021946], time:0.02430797ms
        out_f32_th: [-1.08919787, -1.8021946], time:0.02425861ms
-------------------------------------------------------------------------------------
           out_f16: [-1.08886719, -1.80175781], time:0.02227569ms
         out_f16x2: [-1.08886719, -1.80175781], time:0.01926184ms
         out_f16x8: [-1.08886719, -1.80175781], time:0.01773334ms
     out_f16x8pack: [-1.08886719, -1.80175781], time:0.01068354ms
        out_f16_th: [-1.08886719, -1.80175781], time:0.01049089ms
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------
                                        S=4096, K=4096
           out_f32: [0.9966324, 2.50321245], time:0.28303432ms
         out_f32x4: [0.9966324, 2.50321245], time:0.28802609ms
        out_f32_th: [0.9966324, 2.50321245], time:0.29519820ms
-------------------------------------------------------------------------------------
           out_f16: [0.99658203, 2.50390625], time:0.07408071ms
         out_f16x2: [0.99658203, 2.50390625], time:0.05362153ms
         out_f16x8: [0.99658203, 2.50390625], time:0.05406880ms
     out_f16x8pack: [0.99658203, 2.50390625], time:0.05133891ms
        out_f16_th: [0.99658203, 2.50390625], time:0.05031800ms
-------------------------------------------------------------------------------------
```
