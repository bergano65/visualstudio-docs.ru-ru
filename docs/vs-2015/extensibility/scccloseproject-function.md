---
title: Функция SccCloseProject | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1f689b149ed48b36143e1d18ced3004bb4b17d68
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825380"
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

