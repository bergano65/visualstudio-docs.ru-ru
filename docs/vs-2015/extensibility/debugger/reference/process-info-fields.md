---
title: PROCESS_INFO_FIELDS | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7700670774dcb38b054cf28275f64c0c3046f741
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205026"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает, какой тип сведений необходимо получить для процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
typedef DWORD PROCESS_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
```  
  
## <a name="members"></a>Участники  
 PIF_FILE_NAME  
 Инициализируйте или используйте `bstrFileName` поле структуры [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) .  
  
 PIF_BASE_NAME  
 Инициализируйте или используйте `bstrBaseName` поле `PROCESS_INFO` структуры.  
  
 PIF_TITLE  
 Инициализируйте или используйте `bstrTitle` поле `PROCESS_INFO` структуры.  
  
 PIF_PROCESS_ID  
 Инициализируйте или используйте `ProcessId` поле `PROCESS_INFO` структуры.  
  
 PIF_SESSION_ID  
 Инициализируйте или используйте `dwSessionId` поле `PROCESS_INFO` структуры.  
  
 PIF_ATTACHED_SESSION_NAME  
 Инициализируйте или используйте `bstrAttachedSessionName` поле `PROCESS_INFO` структуры.  
  
 PIF_CREATION_TIME  
 Инициализируйте или используйте `CreationTime` поле `PROCESS_INFO` структуры.  
  
 PIF_FLAGS  
 Инициализируйте или используйте `Flags` поле `PROCESS_INFO` структуры.  
  
 PIF_ALL  
 Заполняет все поля.  
  
## <a name="remarks"></a>Remarks  
 Передается в метод " [info](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) ", чтобы указать, какие поля структуры [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) должны быть инициализированы.  
  
 Также используется в `Fields` поле структуры, `PROCESS_INFO` чтобы указать, какие поля используются и являются допустимыми.  
  
 Эти флаги можно сочетать с помощью побитовой операции `OR` .  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
