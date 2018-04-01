---
title: IDebugClassField::DoesInterfaceExist | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8d0e4535417f80198f06cb6b4255fea209b701e8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Определяет, если конкретный интерфейс определен в классе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```csharp  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszInterfaceName`  
 [in] Строка, содержащая имя интерфейса, для поиска.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK, возвращает значение S_FALSE, если интерфейс существует; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод фактически возвращает перечисление всех интерфейсов и выполняет поиск соответствующего интерфейса по списку.  
  
## <a name="see-also"></a>См. также  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)