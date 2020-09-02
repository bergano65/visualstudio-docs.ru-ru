---
title: 'Идиастакквалкер:: Жетенумфрамес | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames method
ms.assetid: f9f09729-4c34-441c-989c-e0b7339ee32c
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cbad02474af48ac4da72784659dd27007211e64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144711"
---
# <a name="idiastackwalkergetenumframes"></a>IDiaStackWalker::getEnumFrames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает перечислитель кадров стека для платформ x86.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT getEnumFrames(   
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pHelper`  
 окне Вспомогательный объект [идиастакквалкхелпер](../../debugger/debug-interface-access/idiastackwalkhelper.md) .  
  
 `ppEnum`  
 заполняет Возвращает объект [идиаенумстаккфрамес](../../debugger/debug-interface-access/idiaenumstackframes.md) , содержащий список объектов [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Чтобы получить список кадров стека на любой другой платформе, вызовите метод [идиастакквалкер:: getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) .  
  
## <a name="see-also"></a>См. также:  
 [идиастакквалкер](../../debugger/debug-interface-access/idiastackwalker.md)   
 [идиастакквалкхелпер](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)
