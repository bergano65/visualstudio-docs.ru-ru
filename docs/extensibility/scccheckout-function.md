---
title: "Функция SccCheckout | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccCheckout
helpviewer_keywords: SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: af8aac642ecd21f8f4709874e4e3e6ff0b3e58b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="scccheckout-function"></a>Функция SccCheckout
Получает список имен полным путем к файлу, эта функция извлекает их на локальный диск. Комментарий применяется ко всем файлам, извлечения. Аргумент примечания могут быть `null` строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccCheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pvContext  
 [in] Исходная структура подключаемого модуля контекста элемента управления.  
  
 hWnd  
 [in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для все диалоговые окна, которые он предоставляет.  
  
 nFiles  
 [in] Число файлов, выбранных для извлечения.  
  
 lpFileNames  
 [in] Массив имен файлов для извлечения неполный локальный путь.  
  
 lpComment  
 [in] Комментарий для применения к каждой из выбранных извлекаемых файлов.  
  
 fOptions  
 [in] Команда флагов (см. [битовые флаги, используемые определенные команды](../extensibility/bitflags-used-by-specific-commands.md)).  
  
 pvOptions  
 [in] Параметры для конкретного подключаемого модуля системы управления версиями.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Извлечение выполнено успешно.|  
|SCC_E_FILENOTCONTROLLED|Выбранный файл не существует в системе управления версиями.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|  
|SCC_E_NOTAUTHORIZED|Для выполнения этой операции не разрешено пользователю.|  
|SCC_E_NONSPECIFICERROR|Неспецифичную сбоя. Файл не извлечен.|  
|SCC_E_ALREADYCHECKEDOUT|У пользователя уже есть файл извлечен.|  
|SCC_E_FILEISLOCKED|Файл заблокирован запрещения создания новых версий.|  
|SCC_E_FILEOUTEXCLUSIVE|Другой пользователь выполнит монопольного извлечения на этот файл.|  
|SCC_I_OPERATIONCANCELED|Операция отменена до завершения.|  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [Битовые флаги, используемые конкретными командами](../extensibility/bitflags-used-by-specific-commands.md)