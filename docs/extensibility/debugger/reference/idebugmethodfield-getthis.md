---
title: IDebugMethodField::GetThis | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fdb9e0c1503ad924c642d4f6c70b505a99874b4a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035319"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Получает `this` (`Me` в [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]) указатель на объект, содержащий метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetThis(   
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetThis(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppClass`  
 [out] Возвращает [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) объект, представляющий указатель «this».  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 В объектно ориентированных языках обычно имеется неявный указатель указывает на текущий экземпляр класса. Этот процесс называется `this` в C# / C++ и в качестве `Me` в [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].  
  
## <a name="see-also"></a>См. также  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)