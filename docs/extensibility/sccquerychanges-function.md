---
title: "Функция SccQueryChanges | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccQueryChanges
helpviewer_keywords: SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 589013b996f9ed018e28292a27c6a760eef1dae7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="sccquerychanges-function"></a>Функция SccQueryChanges
Эта функция Перечисляет заданный список файлов, предоставляя сведения об изменениях имени для каждого файла через функцию обратного вызова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccQueryChanges(  
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
 [in] Массив имен файлов, о котором требуется получить сведения.  
  
 pfnCallback  
 [in] Функция обратного вызова вызывается для каждого имени файла в списке (см. [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) подробные сведения).  
  
 pvCallerData  
 [in] Без изменений значение, которое будет передано в функцию обратного вызова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Процесс запроса, успешно завершена.|  
|SCC_E_PROJNOTOPEN|Проект не был открыт в системе управления версиями.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов.|  
|SCC_E_NONSPECIFICERROR|Произошла ошибка не задано или Общие.|  
  
## <a name="remarks"></a>Примечания  
 Запрашиваемый для изменения относятся к пространству имен: в частности, переименование, добавление и удаление файла.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [Коды ошибок](../extensibility/error-codes.md)