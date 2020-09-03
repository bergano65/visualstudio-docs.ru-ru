---
title: PROVIDER_PROCESS_DATA | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 89192d814ccee3dd2a134807d8ce01880689d951
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204935"
---
# <a name="provider_process_data"></a>PROVIDER_PROCESS_DATA
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Эта структура предоставляет сведения о процессах, выполняемых на компьютере.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef struct tagPROVIDER_PROCESS_DATA {  
   PROVIDER_FIELDS    Fields;  
   PROGRAM_NODE_ARRAY ProgramNodes;  
   BOOL               fIsDebuggerPresent;  
} PROVIDER_PROCESS_DATA;  
```  
  
```csharp  
public struct PROVIDER_PROCESS_DATA {  
   public uint               Fields;  
   public PROGRAM_NODE_ARRAY ProgramNodes;  
   public int                fIsDebuggerPresent;  
}  
```  
  
## <a name="members"></a>Участники  
 Поля  
 Сочетание флагов из перечисления [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) , указывающее, какие поля заполняются.  
  
 програмнодес  
 Структура [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) , содержащая массив узлов программы.  
  
 фисдебугжерпресент  
 Ненулевое `TRUE` значение () [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] , если отладчик работает, ноль (), если это не так `FALSE` .  
  
## <a name="remarks"></a>Remarks  
 Эта структура передается в метод [жетпровидерпроцессдата](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) , где она заполнена.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)   
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
