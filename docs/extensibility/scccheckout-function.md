---
title: Функция SccCheckout | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 671e4ecebb44f0910eba3bb835a6da6f9a7f3903
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
  
|Значение|Описание|  
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