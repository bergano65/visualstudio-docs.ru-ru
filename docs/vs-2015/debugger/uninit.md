---
title: UnInit | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b5a2accd628cd76c259e1397d99bef255b1b23f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721151"
---
# <a name="uninit"></a>UnInit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Финализирует файл журнала графики, закрывает его и освобождает все ресурсы, которые использовались во время активной записи данных графики приложением.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
void UnInit();  
```  
  
## <a name="remarks"></a>Примечания  
 `UnInit` вызывается автоматически при уничтожении экземпляра класса `VsgDbg`. Если экземпляр `VsgDbg` не вел активной записи данных графики, ничего не происходит.  
  
 После вызова `UnInit` для экземпляра `VsgDbg` новый файл журнала графики можно создать вызовом `Init` и финализировать вызовом `UnInit`. Это действие можно повторять сколько раз, сколько вы хотите использовать один и тот же экземпляр `VsgDbg` для создания нескольких независимых файлов журнала графики.  
  
## <a name="see-also"></a>См. также  
 [Init](../debugger/init.md)



