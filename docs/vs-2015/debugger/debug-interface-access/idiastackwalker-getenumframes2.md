---
title: IDiaStackWalker::getEnumFrames2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 25090ae66d28ebd9eb62f62f14979de1e82c5302
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993273"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает перечислитель кадр стека для типа конкретную платформу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
  
      HRESULT getEnumFrames2(   
   enum  CV_CPU_TYPE_e    cpuid,  
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cpuid`  
 [in] Значение из [перечисление CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) перечисления, указывающее тип платформы.  
  
 `pHelper`  
 [in] Вспомогательный метод [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) объекта.  
  
 `ppEnum`  
 [out] Возвращает [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) объект, содержащий список [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) объектов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Для получения списка кадр стека для только что x86 платформы, вызов [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [Перечисление CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
