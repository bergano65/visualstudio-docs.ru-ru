---
title: THREADPROPERTY_FIELDS | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc0e0f7cae4aed887809c22bda0cd6a9ed50307f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204809"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает, какие сведения о потоке необходимо получить.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```csharp  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Участники  
 TPF_ID  
 Инициализируйте или используйте `dwThreadId` поле структуры [среадпропертиес](../../../extensibility/debugger/reference/threadproperties.md) .  
  
 TPF_SUSPENDCOUNT  
 Инициализируйте или используйте `dwSuspendCount` поле `THREADPROPERTIE` структуры S.  
  
 TPF_STATE  
 Инициализируйте или используйте `dwThreadState` поле `THREADPROPERTIE` структуры S.  
  
 TPF_PRIORITY  
 Инициализируйте или используйте `bstrPriority` поле `THREADPROPERTIE` структуры S.  
  
 TPF_NAME  
 Инициализируйте или используйте `bstrName` поле `THREADPROPERTIE` структуры S.  
  
 TPF_LOCATION  
 Инициализируйте или используйте `bstrLocation` поле `THREADPROPERTIE` структуры S.  
  
 TPF_ALLFIELDS  
 Задает все поля.  
  
## <a name="remarks"></a>Remarks  
 Эти значения передаются в качестве аргумента в метод [жетсреадпропертиес](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) , чтобы указать, какие поля структуры [среадпропертиес](../../../extensibility/debugger/reference/threadproperties.md) должны быть инициализированы.  
  
 Эти значения также используются в `dwFields` члене `THREADPROPERTIES` структуры для указания того, какие поля используются и являются допустимыми.  
  
 Эти флаги можно сочетать с помощью побитовой операции `OR` .  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [среадпропертиес](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
