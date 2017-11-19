---
title: "SEEK_START | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SEEK_START
helpviewer_keywords: SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 10937c4a5078574f7658bc54f2508b576209f9d5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="seekstart"></a>SEEK_START
Указывает положение, с которого следует начать поиск в потоке Дизассемблированный код.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
typedef DWORD SEEK_START;  
```  
  
```csharp  
public enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
```  
  
## <a name="members"></a>Члены  
 SEEK_START_BEGIN  
 Начинает поиск с начала текущего документа.  
  
 SEEK_START_END  
 Начинает поиск в конце текущего документа.  
  
 SEEK_START_CURRENT  
 Начинает поиск в текущей позиции текущего документа.  
  
 SEEK_START_CODECONTEXT  
 Начинает поиск в контексте данного кода текущего документа.  
  
 SEEK_START_CODELOCID  
 Запускает поиск на расположение идентификатора данного кода. Идентификаторы расположение кода можно получить путем вызова [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).  
  
## <a name="remarks"></a>Примечания  
 Передается в качестве аргумента для [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Поиск](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)   
 [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)