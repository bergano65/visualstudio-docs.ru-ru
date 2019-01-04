---
title: IDebugProcessQueryProperties::QueryProperty | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessQueryProperties::QueryProperty
ms.assetid: 9a91707d-a590-44ef-b122-69d9816a7a79
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7cef004072af51f0e564dcc860ad10c773354aba
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53966788"
---
# <a name="idebugprocessquerypropertiesqueryproperty"></a>IDebugProcessQueryProperties::QueryProperty
Этот метод запрашивает значение указанного свойства процесса отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT QueryProperty(  
   PROCESS_PROPERTY_TYPE  dwPropType,  
   VARIANT               *pvarPropValue);  
```  
  
```csharp  
int QueryProperty(  
   enum_PROCESS_PROPERTY_TYPE dwPropType,  
   out object                 pvarPropValue);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwPropType`  
 [in] Определение свойства запроса. Возможные значения:  
  
- PROCESS_PROPERTY_COMMAND_LINE = 1  
  
- PROCESS_PROPERTY_CURRENT_DIRECTORY = 2  
  
- PROCESS_PROPERTY_ENVIRONMENT_VARIABLES = 3  
  
  `pvarPropValue`  
  [out] Значение свойства.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод используется редко.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcessQueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties.md)