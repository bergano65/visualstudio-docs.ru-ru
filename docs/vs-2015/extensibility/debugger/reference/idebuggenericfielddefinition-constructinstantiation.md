---
title: IDebugGenericFieldDefinition::ConstructInstantiation | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c5bd1d6164019414bc7cc299e418c38365dbc95
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572345"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugGenericFieldDefinition::ConstructInstantiation](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation).  
  
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

