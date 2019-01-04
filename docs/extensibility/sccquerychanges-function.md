---
title: Функция SccQueryChanges | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d6fabc1108f82c1cd2b43bf740e58c4ea9bb613e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910887"
---
# <a name="sccquerychanges-function"></a>Функция SccQueryChanges
Эта функция Перечисляет заданный список файлов, предоставляя сведения об изменениях имени для каждого файла через функцию обратного вызова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pContext  
 [in] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 nFiles  
 [in] Число файлов в `lpFileNames` массива.  
  
 lpFileNames  
 [in] Массив имен файлов требуется получить сведения.  
  
 pfnCallback  
 [in] Функция обратного вызова для вызова для каждого имени файла в списке (см. в разделе [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) сведения).  
  
 pvCallerData  
 [in] Без изменений значение, которое будет передано в функцию обратного вызова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Процесс запроса успешно завершена.|  
|SCC_E_PROJNOTOPEN|Проект не был открыт в системе управления версиями.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов.|  
|SCC_E_NONSPECIFICERROR|Произошла ошибка не задано или Общие.|  
  
## <a name="remarks"></a>Примечания  
 Запрашиваемый для изменяются на пространство имен: в частности, переименование, добавление и удаление файла.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [Коды ошибок](../extensibility/error-codes.md)