---
title: Функция SccCloseProject | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a872d02abd10a024fe4f636ca21320ecbced4f50
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53883696"
---
# <a name="scccloseproject-function"></a>Функция SccCloseProject
Эта функция закрывает проект, отмечающую конец конкретного сеанса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
### <a name="parameters"></a>Параметры  
 pvContext  
 Структура подключаемого модуля контекста исходного элемента управления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Проект был успешно закрыт.|  
|SCC_E_PROJNOTOPEN|Проект не открыт.|  
|SCC_E_NOTAUTHORIZED|Пользователю запрещено для этой операции.|  
|SCC_E_NONSPECIFICERROR|Обнаружена неспецифическая ошибка.|  
  
## <a name="remarks"></a>Примечания  
 [SccOpenProject](../extensibility/sccopenproject-function.md) всегда вызывается перед этой функцией. Вызов этой функции выполняется путем вызова либо `SccOpenProject` функции или [SccUninitialize](../extensibility/sccuninitialize-function.md), для завершения подключения к системе управления версиями, полностью.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)