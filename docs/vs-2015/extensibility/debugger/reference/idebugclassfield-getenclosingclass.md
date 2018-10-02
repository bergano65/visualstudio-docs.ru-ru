---
title: IDebugClassField::GetEnclosingClass | Документация Майкрософт
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
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 34648ee01b1aaa070dea779777095bda98133211
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559250"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugClassField::GetEnclosingClass](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugclassfield-getenclosingclass).  
  
Возвращает класс, который содержит этот класс.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```csharp  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppClassField`  
 [out] Возвращает [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) объект, представляющий включающий класс. Возвращает значение null, если нет включающего класса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если класс, представленный это [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) объекта является вложенным классом, а затем `ppClassField` параметр возвращает `IDebugClassField` объект, представляющий включающий класс. Например рассмотрим следующее определение класса:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Вызов `GetEnclosingClass` метод `IDebugClassField` объект, представляющий `NestedClass` возвращает `IDebugClassField` объект, представляющий класс `RootClass`.  
  
## <a name="see-also"></a>См. также  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)

