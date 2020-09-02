---
title: 'IDebugCustomAttributeQuery2:: Жеткустоматтрибутебинаме | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e1af059cf4319c18b8f8bb63e7b50ec3d2822e93
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568438"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получает байты пользовательских атрибутов с учетом имени настраиваемого атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```csharp  
int GetCustomAttributeByName(  
   [In] string        pszCustomAttributeName,   
   [In, Out] byte[]   ppBlob,   
   [In, Out] ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszCustomAttributeName`  
 окне Строка, содержащая имя настраиваемого атрибута для поиска.  
  
 `ppBlob`  
 [вход, выход] Массив, который заполняется байтами настраиваемого атрибута.  
  
 `pdwLen`  
 [вход, выход] Указывает максимальное число байтов, возвращаемых в `ppBlob` массиве, и возвращает число байтов, фактически записанных в массив.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK или возвращает значение, S_FALSE, если пользовательский атрибут не существует. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Установите `ppBlob` для параметра значение null, чтобы получить количество доступных атрибутов в байтах. Затем выделите массив и передайте этот массив в `ppBlob` параметр.  
  
 Байты атрибутов представляют необработанные данные настраиваемого атрибута.  
  
 Если `ppBlob` `pdwLen` для параметров и задано значение null, этот метод можно использовать, чтобы определить, существует ли пользовательский атрибут. Однако проще альтернативой является вызов метода [искустоматтрибутедефинед](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
