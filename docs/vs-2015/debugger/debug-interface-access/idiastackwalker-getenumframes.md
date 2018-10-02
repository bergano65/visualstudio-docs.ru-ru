---
title: IDiaStackWalker::getEnumFrames | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames method
ms.assetid: f9f09729-4c34-441c-989c-e0b7339ee32c
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6afbedb02a614597ddd499706e3ee933142871b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563161"
---
# <a name="idiastackwalkergetenumframes"></a>IDiaStackWalker::getEnumFrames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaStackWalker::getEnumFrames](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackwalker-getenumframes).  
  
Извлекает перечислитель кадр стека для x86 платформ.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT getEnumFrames(   
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pHelper`  
 [in] Вспомогательный метод [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) объекта.  
  
 `ppEnum`  
 [out] Возвращает [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) , содержащий список [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) объектов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Чтобы получить список кадров стека в любой другой платформы, вызовите [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)



