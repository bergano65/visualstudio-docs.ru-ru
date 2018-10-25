---
title: GETNAME_TYPE | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 40ee5cb4bf552b04683c4c2119a8c43a595b2105
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900310"
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
 Указывает понятное имя документа или контекста.  
  
 GN_FILENAME  
 Указывает полный путь документа или контекста.  
  
 GN_BASENAME  
 Указывает имя базового файла, а не полный путь документа или контекста.  
  
 GN_MONIKERNAME  
 Указывает уникальное имя документа или контекста в виде моникер.  
  
 GN_URL  
 Задает имя URL-адрес документа или контекста.  
  
 GN_TITLE  
 Указывает заголовок документа, если он существует.  
  
 GN_STARTPAGEURL  
 Получает URL-адрес начальной страницы для процессов.  
  
## <a name="remarks"></a>Примечания  
 Эти значения передаются как параметры для [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md), и [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) методы, чтобы указать, какие имени для возврата.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)