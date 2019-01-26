---
title: IDebugDocument2::GetName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 393caa58960795b29abe1389a8f8340643f6c9de
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929670"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Возвращает имя документа в одну из нескольких форм.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetName(   
   GETNAME_TYPE gnType,  
   BSTR*        pbstrFileName  
);  
```  
  
```csharp  
int GetName(   
   enum_GETNAME_TYPE gnType,  
   out string        pbstrFileName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `gnType`  
 [in] Значение из [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) перечисление, определяющее тип имени для возврата.  
  
 `pbstrFileName`  
 [out] Возвращает строку, содержащую имя документа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод можно например, возвращать имя документа, как заголовок или имя файла или даже частью имени файла.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)