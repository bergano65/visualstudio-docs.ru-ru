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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444955"
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
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
 ulAppDomainID  
 Идентификатор процесса.  
  
 guidModule  
 Идентификатор GUID модуля, содержащего этот адрес.  
  
 tokClass  
 Токен, идентифицирующий класс или тип этого адреса.  
  
> [!NOTE]
> Это значение относится к поставщика символов и поэтому не имеет общие значения отличное от как идентификатор для типа класса.  
  
 Addr  
 Объект [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) структуру, которая содержит объединение структур, которые описывают типы отдельных адресов. Значение `addr`.`dwKind` поступает из [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) перечисления, который объясняет, как интерпретировать объединение.  
  
## <a name="remarks"></a>Примечания  
 Эта структура передается [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) метод для заполнения.  
  
 **Предупреждение [C++ только]**  
  
 Если `addr.dwKind` — `ADDRESS_KIND_METADATA_LOCAL` и если `addr.addr.addrLocal.pLocal` не имеет значение null, то нужно вызвать `Release` маркеров указателя:  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
