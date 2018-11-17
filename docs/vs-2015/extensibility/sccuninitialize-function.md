---
title: Функция SccUninitialize | Документация Майкрософт
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
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f81bb0cd478320b7fa6b5faee28e79ad1dcb0642
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736256"
---
# <a name="sccuninitialize-function"></a>Функция SccUninitialize
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта функция очищает все выделения или открытых подключений, созданных предыдущим вызовом [SccInitialize](../extensibility/sccinitialize-function.md) в ожидании завершения работы подключаемого модуля системы управления версиями.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pvContext  
 [in] Указатель на структуру исходного элемента управления контекста подключаемый модуль создан в [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Очистка завершена успешно.|  
  
## <a name="remarks"></a>Примечания  
 Подключаемый модуль системы управления версиями ответственность за освобождение памяти, выделенной подключаемый модуль для структура контекста и завершает работу. Функция вызывается один раз для каждого заданного экземпляра подключаемого модуля. Вызов [SccInitialize](../extensibility/sccinitialize-function.md) предшествует этот вызов. Нет проектов по-прежнему могут быть открыты во время вызова `SccUninitialize`.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)

