---
title: Функция Сккклосепрожект | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156134"
---
# <a name="scccloseproject-function"></a>Функция SccCloseProject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта функция закрывает проект, помечая конец конкретного сеанса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 пвконтекст  
 Структура контекста подключаемого модуля системы управления версиями.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Проект успешно закрыт.|  
|SCC_E_PROJNOTOPEN|В настоящий момент нет открытых проектов.|  
|SCC_E_NOTAUTHORIZED|Пользователю не разрешено выполнять эту операцию.|  
|SCC_E_NONSPECIFICERROR|Неконкретный сбой.|  
  
## <a name="remarks"></a>Remarks  
 [Сккопенпрожект](../extensibility/sccopenproject-function.md) всегда вызывается перед этой функцией. После вызова этой функции следует вызов `SccOpenProject` функции или [сккунинитиализе](../extensibility/sccuninitialize-function.md), который полностью завершает подключение к системе управления версиями.  
  
## <a name="see-also"></a>См. также:  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)   
 [сккопенпрожект](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
