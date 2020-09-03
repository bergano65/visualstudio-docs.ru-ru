---
title: Функция Сккунинитиализе | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bcb0b3a6718cc90db6f7176c823ccccbbfc05f9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190846"
---
# <a name="sccuninitialize-function"></a>Функция SccUninitialize
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта функция очищает все выделения или открытые соединения, созданные с помощью предыдущего вызова [скЦинитиализе](../extensibility/sccinitialize-function.md) , при подготовке к завершению работы подключаемого модуля системы управления версиями.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 пвконтекст  
 окне Указатель на структуру контекста подключаемого модуля системы управления версиями, созданную в [скЦинитиализе](../extensibility/sccinitialize-function.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Очистка успешно завершена.|  
  
## <a name="remarks"></a>Remarks  
 Подключаемый модуль системы управления версиями отвечает за подготовку к завершению работы и освобождение памяти, выделенной подключаемым модулем для структуры контекста. Функция вызывается один раз для каждого заданного экземпляра подключаемого модуля. Вызов [скЦинитиализе](../extensibility/sccinitialize-function.md) предшествует этому вызову. Проекты по-прежнему не могут быть открыты во время вызова `SccUninitialize` .  
  
## <a name="see-also"></a>См. также:  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
