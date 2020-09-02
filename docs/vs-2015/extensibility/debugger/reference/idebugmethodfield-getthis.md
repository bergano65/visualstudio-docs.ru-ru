---
title: 'Идебугмесодфиелд:: onthis | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 786f3986875518470ed5756a0f7b57f4f93f5ca2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62563615"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает `this` указатель ( `Me` в [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] ) объекта, содержащего метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 заполняет Возвращает объект [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md) , представляющий указатель this.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 В объектно-ориентированных языках обычно существует подразумеваемый указатель на текущий экземпляр класса. Это называется `this` в C#/c + + и, как `Me` в [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [идебугмесодфиелд](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
