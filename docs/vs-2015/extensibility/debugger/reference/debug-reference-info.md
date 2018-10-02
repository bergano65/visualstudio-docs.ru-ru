---
title: DEBUG_REFERENCE_INFO | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0fc0819e323e477fea8e2cc3ba2cddb6338c2861
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571466"
---
# <a name="debugreferenceinfo"></a>DEBUG_REFERENCE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [DEBUG_REFERENCE_INFO](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/debug-reference-info).  
  
Описывает ссылку.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef struct tagDEBUG_REFERENCE_INFO {   
   DEBUGREF_INFO_FLAGS dwFields;  
   BSTR                bstrName;  
   BSTR                bstrType;  
   BSTR                bstrValue;  
   DBG_ATTRIB_FLAGS    dwAttrib;  
   REFERENCE_TYPE.     dwRefType;  
   IDebugReference2*   m_pReference;  
} DEBUG_REFERENCE_INFO;  
```  
  
```csharp  
public struct DEBUG_REFERENCE_INFO {   
   public uint             dwFields;  
   public string           bstrName;  
   public string           bstrType;  
   public string           bstrValue;  
   public ulong            dwAttrib;  
   public uint.            dwRefType;  
   public IDebugReference2 m_pReference;  
};  
```  
  
## <a name="members"></a>Участники  
 dwFields  
 Сочетание флагов из [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) перечисление, указывающее, какие поля заполнены.  
  
 bstrName  
 Определяемое пользователем имя [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) объекта.  
  
 bstrType  
 Ссылочный тип, как отформатированную строку.  
  
 bstrValue  
 Значение ссылки как отформатированную строку  
  
 dwAttrib  
 Сочетание флагов из [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) перечисление, указывающее флаги для атрибутов свойства отладки.  
  
 dwRefType  
 Значение из [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) перечисление, указывающее, является ли тип ссылки строгие или слабые.  
  
 m_pReference  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , указывающий справочные сведения.  
  
## <a name="remarks"></a>Примечания  
 Эта структура передается в вызов [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) метод для заполнения. Эта структура также возвращается как часть списка из [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) интерфейс, который, в свою очередь, возвращается из вызова [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)

