---
title: Функция Сккчеккаут | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f23290ebfadd1b6e3d34f808d5ea0ccccbb3c319
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200154"
---
# <a name="scccheckout-function"></a>Функция SccCheckout
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При наличии списка полных имен файлов Эта функция проверяет их на локальном диске. Комментарий применяется ко всем извлеченным файлам. Аргумент комментария может быть `null` строкой.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 пвконтекст  
 окне Структура контекста подключаемого модуля системы управления версиями.  
  
 hWnd  
 окне Обработчик окна интегрированной среды разработки, который может использоваться подключаемым модулем системы управления версиями в качестве родительского для любых предоставляемых им диалоговых окон.  
  
 Nфайлы оставленные  
 окне Число выбранных файлов для извлечения.  
  
 лпфиленамес  
 окне Массив полных имен локальных путей к извлекаемым файлам.  
  
 лпкоммент  
 окне Комментарий, применяемый к каждому из выбранных файлов, которые будут извлечены.  
  
 фоптионс  
 окне Флаги команды (см. раздел [битфлагс, используемый конкретными командами](../extensibility/bitflags-used-by-specific-commands.md)).  
  
 пвоптионс  
 окне Параметры, зависящие от подключаемого модуля системы управления версиями.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Извлечение успешно выполнено.|  
|SCC_E_FILENOTCONTROLLED|Выбранный файл не находится под управлением исходного кода.|  
|SCC_E_ACCESSFAILURE|Возникла проблема при доступе к системе управления версиями, возможно, из-за проблем с сетью или состязаниями. Рекомендуется повторить попытку.|  
|SCC_E_NOTAUTHORIZED|Пользователю не разрешено выполнять эту операцию.|  
|SCC_E_NONSPECIFICERROR|Неконкретный сбой. Файл не был извлечен.|  
|SCC_E_ALREADYCHECKEDOUT|Файл уже извлечен пользователем.|  
|SCC_E_FILEISLOCKED|Файл заблокирован, создание новых версий запрещено.|  
|SCC_E_FILEOUTEXCLUSIVE|Другой пользователь выполнил монопольное извлечение этого файла.|  
|SCC_I_OPERATIONCANCELED|Операция была отменена до завершения.|  
  
## <a name="see-also"></a>См. также:  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)   
 [Битовые флаги, используемые конкретными командами](../extensibility/bitflags-used-by-specific-commands.md)
