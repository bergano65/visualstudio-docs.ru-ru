---
title: Функция SccQueryChanges | Документация Майкрософт
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
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 95f1e5a21ba74779080c601acd42d5deedb75d7c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562934"
---
# <a name="sccquerychanges-function"></a>Функция SccQueryChanges
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [функция SccQueryChanges](https://docs.microsoft.com/visualstudio/extensibility/sccquerychanges-function).  
  
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
 [in] Массив имен файлов требуется получить сведения.  
  
 pfnCallback  
 [in] Функция обратного вызова для вызова для каждого имени файла в списке (см. в разделе [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) сведения).  
  
 pvCallerData  
 [in] Без изменений значение, которое будет передано в функцию обратного вызова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
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

