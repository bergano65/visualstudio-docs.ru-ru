---
title: Функция SccCheckout | Документация Майкрософт
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
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ad6621b2a7e4493883bf3639f388a76fa4e552fa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210547"
---
# <a name="scccheckout-function"></a>Функция SccCheckout
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При наличии списка имен полного имени файла, эта функция извлекает их на локальный диск. Комментарий применяется ко всем файлам, проверяемого товара. Аргумент примечания могут быть `null` строка.  
  
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
 pvContext  
 [in] Структура подключаемого модуля контекста исходного элемента управления.  
  
 hWnd  
 [in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для любой диалоговых окон, которые он предоставляет.  
  
 nFiles  
 [in] Число файлов, выбранных для извлечения.  
  
 lpFileNames  
 [in] Массив имен файлов для извлечения полный локальный путь.  
  
 lpComment  
 [in] Комментарий для применения к каждой из выбранных файлов, проверяемого товара.  
  
 Возможности  
 [in] Команда флагов (см. в разделе [битовые флаги, используемые конкретными командами](../extensibility/bitflags-used-by-specific-commands.md)).  
  
 pvOptions  
 [in] Параметры конкретного подключаемого модуля системы управления версиями.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Извлечение выполнено успешно.|  
|SCC_E_FILENOTCONTROLLED|Выбранный файл не существует в системе управления версиями.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|  
|SCC_E_NOTAUTHORIZED|Пользователю запрещено для этой операции.|  
|SCC_E_NONSPECIFICERROR|Обнаружена неспецифическая ошибка. Файл не был извлечен.|  
|SCC_E_ALREADYCHECKEDOUT|У пользователя уже есть извлеченный файл.|  
|SCC_E_FILEISLOCKED|Файл заблокирован, Запрет создания новых версий.|  
|SCC_E_FILEOUTEXCLUSIVE|Другой пользователь выполнит монопольного извлечения на этот файл.|  
|SCC_I_OPERATIONCANCELED|Операция была отменена до завершения.|  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [Битовые флаги, используемые конкретными командами](../extensibility/bitflags-used-by-specific-commands.md)

