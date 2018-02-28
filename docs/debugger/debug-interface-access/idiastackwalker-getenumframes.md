---
title: "IDiaStackWalker::getEnumFrames | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames method
ms.assetid: f9f09729-4c34-441c-989c-e0b7339ee32c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 908c6d172a0219d17353701ae13c807f78bc11e8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiastackwalkergetenumframes"></a>IDiaStackWalker::getEnumFrames
Извлекает перечислитель кадр стека для x86 платформы.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT getEnumFrames(   
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pHelper`  
 [in] Вспомогательный объект [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) объекта.  
  
 `ppEnum`  
 [out] Возвращает [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) , содержащий список [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) объектов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Чтобы получить список кадров стека на любой другой платформы, вызовите [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)