---
title: DEBUG_ADDRESS | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d001d29433573fedde3b4310f989667538b4b69c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843085"
---
# <a name="debug_address"></a>DEBUG_ADDRESS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Эта структура представляет адрес.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```csharp  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## <a name="terms"></a>Термины  
 улаппдомаинид  
 Идентификатор процесса.  
  
 гуидмодуле  
 Идентификатор GUID модуля, содержащего этот адрес.  
  
 токкласс  
 Токен, идентифицирующий класс или тип этого адреса.  
  
> [!NOTE]
> Это значение характерно для поставщика символов и, следовательно, не имеет общего значения, кроме идентификатора типа класса.  
  
 addr  
 Структура [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , которая содержит объединение структур, описывающих отдельные типы адресов. Значение `addr` .`dwKind` поступает из перечисления [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) , в котором объясняется, как интерпретировать объединение.  
  
## <a name="remarks"></a>Remarks  
 Эта структура передается в [метод метода method, который](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) должен быть заполнен.  
  
 **Предупреждение [только C++]**  
  
 Если `addr.dwKind` имеет `ADDRESS_KIND_METADATA_LOCAL` значение и `addr.addr.addrLocal.pLocal` , если не является значением NULL, необходимо вызвать `Release` для указателя токена:  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Выадресовать](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
