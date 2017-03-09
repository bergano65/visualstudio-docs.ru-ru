---
title: "Long Double | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.types"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "двойное с плавающей запятой длиной 10 байт"
  - "16-разрядная Windows"
  - "32-разрядная Windows"
  - "двойное с плавающей запятой длиной 8 байт"
  - "точность 80 бит"
  - "80-битная точность"
  - "двойное с плавающей запятой длиной 8 байт"
  - "long double"
ms.assetid: bb581e20-b5c2-4079-8ee8-ac6739a37852
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Long Double
Предыдущие 16\-разрядные версии Microsoft C\+\+ и Microsoft Visual C\# поддерживали `long double` — тип данных с 80\-разрядной точностью.  Однако в программировании на Win32 тип данных `double` сопоставляется с `long double` — типом данных с 64\-разрядной точностью.  Библиотека среды выполнения Microsoft предоставляет `long double` версии математических функций только для обратной совместимости.  Прототипы функций `long double` совпадают с прототипам их аналогов `double` за исключением того, что тип данных `long` `double` заменяет тип данных `double`.  Версии `long double` этих функций не должны использоваться в новом коде.  
  
### Double функции и их аналоги long double.  
  
|Функция|Long double<br /><br /> аналог|Функция|Long double<br /><br /> аналог|  
|-------------|----------------------------|-------------|----------------------------|  
|[acos](/visual-cpp/c-runtime-library/reference/acos-acosf-acosl)|`acosl`|[frexp](/visual-cpp/c-runtime-library/reference/frexp)|`frexpl`|  
|[asin](/visual-cpp/c-runtime-library/reference/asin-asinf-asinl)|`asinl`|[\_hypot](/visual-cpp/c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl)|`_hypotl`|  
|[atan](/visual-cpp/c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l)|`atanl`|[ldexp](/visual-cpp/c-runtime-library/reference/ldexp)|`ldexpl`|  
|[atan2](/visual-cpp/c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l)|`atan2l`|[log](/visual-cpp/c-runtime-library/reference/log-logf-log10-log10f)|`logl`|  
|[atof](/visual-cpp/c-runtime-library/reference/atof-atof-l-wtof-wtof-l)|`_atold`|[log10](/visual-cpp/c-runtime-library/reference/log-logf-log10-log10f)|`log10l`|  
|[Функции Бесселя: j0, j1, jn](../misc/bessel-functions-j0-j1-jn.md)|`j0l, j1l, jnl`|[\_matherr](/visual-cpp/c-runtime-library/reference/matherr)|`_matherrl`|  
|[Функции Бесселя: y0, y1, yn](../Topic/Bessel%20Functions:%20_y0,%20_y1,%20_yn.md)|`y0l, y1l, ynl`|[modf](/visual-cpp/c-runtime-library/reference/modf-modff-modfl)|`modfl`|  
|[\_cabs](/visual-cpp/c-runtime-library/reference/cabs)|`_cabsl`|[pow](/visual-cpp/c-runtime-library/reference/pow-powf-powl)|`powl`|  
|[ceil](/visual-cpp/c-runtime-library/reference/ceil-ceilf-ceill)|`ceill`|[sin](/visual-cpp/c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl)|`sinl`|  
|[cos](/visual-cpp/c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl)|`cosl`|[sinh](/visual-cpp/c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl)|`sinhl`|  
|[cosh](/visual-cpp/c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl)|`coshl`|[sqrt](/visual-cpp/c-runtime-library/reference/sqrt-sqrtf-sqrtl)|`sqrtl`|  
|[exp](/visual-cpp/c-runtime-library/reference/exp-expf)|`expl`|[strtod](/visual-cpp/c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l)|`_strtold`|  
|[fabs](/visual-cpp/c-runtime-library/reference/fabs-fabsf-fabsl)|`fabsl`|[tan](/visual-cpp/c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl)|`tanl`|  
|[floor](/visual-cpp/c-runtime-library/reference/floor-floorf-floorl)|`floorl`|[tanh](/visual-cpp/c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl)|`tanhl`|  
|[fmod](/visual-cpp/c-runtime-library/reference/fmod-fmodf)|`fmodl`|||  
  
## См. также  
 [Процедуры среды выполнения по категориям](/visual-cpp/c-runtime-library/run-time-routines-by-category)