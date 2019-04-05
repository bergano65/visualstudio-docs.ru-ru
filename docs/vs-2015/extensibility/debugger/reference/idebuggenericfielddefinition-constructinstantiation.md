---
title: IDebugGenericFieldDefinition::ConstructInstantiation | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 57a28cfd3b2ccd2ff37fae80d426817b664972fb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991123"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает экземпляр поля задан массив аргументов типа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT ConstructInstantiation(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   IDebugField** ppConstructedField  
);  
```  
  
```csharp  
int ConstructInstantiation(  
   uint            cArgs,  
   IDebugField[]   ppArgs,  
   out IDebugField ppConstructedField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cArgs`  
 [in] Число аргументов в `ppArgs` массива.  
  
 `ppArgs`  
 [in] Массив, содержащий аргументы типа. Аргументы типа должны быть закрытые типы (универсальные типы неуниверсальных или полностью создать экземпляр).  
  
 `ppConstructedField`  
 [out] Возвращает [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс, представляющий новое поле.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Ограничения не проверяются.  
  
## <a name="see-also"></a>См. также  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
