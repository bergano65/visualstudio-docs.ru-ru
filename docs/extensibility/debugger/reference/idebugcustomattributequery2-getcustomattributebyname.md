---
title: "IDebugCustomAttributeQuery2::GetCustomAttributeByName | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: bc1b59d4f13029a765f11dfd4fe3dbe12778d00c
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Получает настраиваемые атрибуты байт, назначается имя настраиваемого атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```c#  
int GetCustomAttributeByName(  
   [In] string        pszCustomAttributeName,   
   [In, Out] byte[]   ppBlob,   
   [In, Out] ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszCustomAttributeName`  
 [in] Строка, содержащая имя настраиваемого атрибута для поиска.  
  
 `ppBlob`  
 [in, out] Массив, который заполняется байт настраиваемого атрибута.  
  
 `pdwLen`  
 [in, out] Указывает максимальное число байтов для возврата в `ppBlob` массива и возвращает число байтов, записанных в массив.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает значение S_OK, или возвращает значение S_FALSE, если пользовательский атрибут не существует. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Задайте `ppBlob` атрибуты параметра значение null для возврата числа доступных байтов. Затем выделите массив и передайте массив в для `ppBlob` параметр.  
  
 Атрибут байты представляют необработанные данные настраиваемого атрибута.  
  
 Если `ppBlob` и `pdwLen` параметры устанавливаются в значение null, этот метод можно использовать для определения, существует ли просто пользовательский атрибут. Альтернативы проще, тем не менее, заключается в вызове [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
