---
title: IDebugClassField::DoesInterfaceExist | Документация Майкрософт
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
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: af7c4db5d7515d9de49ab8ffda40acfda521a5df
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562780"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugClassField::DoesInterfaceExist](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugclassfield-doesinterfaceexist).  
  
Определяет, если конкретный интерфейс определен в классе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 [in] Строка, содержащая искомое имя интерфейса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK, возвращает S_FALSE, если интерфейс не существует. в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод фактически возвращает перечисление всех интерфейсов и выполняет поиск соответствующего интерфейса по списку.  
  
## <a name="see-also"></a>См. также  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)

