---
title: 'Идиастакквалкер:: getEnumFrames2 | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144720"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает перечислитель кадров стека для определенного типа платформы.  
  
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
 окне Значение из перечисления [перечисления CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) , указывающее тип платформы.  
  
 `pHelper`  
 окне Вспомогательный объект [идиастакквалкхелпер](../../debugger/debug-interface-access/idiastackwalkhelper.md) .  
  
 `ppEnum`  
 заполняет Возвращает объект [идиаенумстаккфрамес](../../debugger/debug-interface-access/idiaenumstackframes.md) , содержащий список объектов [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Чтобы получить список кадров стека только для платформы x86, вызовите метод [идиастакквалкер:: жетенумфрамес](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) .  
  
## <a name="see-also"></a>См. также:  
 [идиастакквалкер](../../debugger/debug-interface-access/idiastackwalker.md)   
 [Перечисление CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [идиастакквалкхелпер](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
