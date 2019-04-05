---
title: Функция SccCloseProject | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7d2364215f528f16d05ecf0c53b152f7334f4b4a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993792"
---
# <a name="scccloseproject-function"></a>Функция SccCloseProject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта функция закрывает проект, отмечающую конец конкретного сеанса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
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
