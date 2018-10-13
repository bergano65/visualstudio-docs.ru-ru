---
title: METADATA_ADDRESS_METHOD | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- METADATA_ADDRESS_METHOD
helpviewer_keywords:
- METADATA_ADDRESS_METHOD structure
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b5eba510d46fecc5fa678fb60b8519e7d9886ff4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245990"
---
# <a name="metadataaddressmethod"></a>METADATA_ADDRESS_METHOD
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Эта структура представляет собой адрес методу класса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_METHOD {  
   _mdToken tokMethod;  
   DWORD    dwOffset;  
   DWORD    dwVersion;  
} METADATA_ADDRESS_METHOD;  
```  
  
```csharp  
public struct METADATA_ADDRESS_METHOD {  
   public int  tokMethod;  
   public uint dwOffset;  
   public uint dwVersion;  
}  
```  
  
## <a name="terms"></a>Термины  
 tokMethod  
 Идентификатор метода.  
  
 [C++] `_mdToken` — `typedef` для 32-разрядных `int`.  
  
 dwOffset  
 Смещение от начала класса в этот метод (может представлять смещения в таблице vtable).  
  
 Версия хранилища данных  
 Версия метода (это значение является уникальным для поставщика символов).  
  
## <a name="remarks"></a>Примечания  
 Эта структура является частью объединения в [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) структуры, когда `dwKind` поле `DEBUG_ADDRESS_UNION` структура присваивается `ADDRESS_KIND_METHOD` (значение из [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Перечисление).  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)

