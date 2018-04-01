---
title: GETNAME_TYPE | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bb73d39aec7f364ce27ab06ef426d1c4a622878a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="getnametype"></a>GETNAME_TYPE
Задает имя тип файлов для извлечения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
typedef DWORD GETNAME_TYPE;  
```  
  
```csharp  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## <a name="members"></a>Участники  
 GN_NAME  
 Указывает понятное имя документа или контекст.  
  
 GN_FILENAME  
 Указывает полный путь документа или контекст.  
  
 GN_BASENAME  
 Указывает имя базового файла вместо полного пути документа или контекст.  
  
 GN_MONIKERNAME  
 Задает уникальное имя документа или контекст в форме специальное имя.  
  
 GN_URL  
 Указывает имя URL-адрес документа или контекст.  
  
 GN_TITLE  
 Указывает заголовок документа, если таковая существует.  
  
 GN_STARTPAGEURL  
 Возвращает URL-адрес начальной страницы для процессов.  
  
## <a name="remarks"></a>Примечания  
 Эти значения передаются как параметры для [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md), и [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) методы, чтобы указать, какие возвращаемого имени.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)