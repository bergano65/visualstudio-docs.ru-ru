---
title: "Функция SccCheckin | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: b082ca831c17dcab3fbc95f8dd547da23a1f8982
ms.contentlocale: ru-ru
ms.lasthandoff: 09/06/2017

---
# <a name="scccheckin-function"></a>Функция SccCheckin
Эта функция проверяет ранее извлеченных файлов в системе управления версиями, сохранение изменений и создание новой версии. Эта функция вызывается с количеством и массив имен файлов для возврата.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pvContext  
 [in] Исходная структура подключаемого модуля контекста элемента управления.  
  
 hWnd  
 [in] Дескриптор окна интегрированной среды разработки, SCC подключаемый модуль можно использовать в качестве родительского для все диалоговые окна, которые он предоставляет.  
  
 nFiles  
 [in] Число файлов, выбранных для возврата.  
  
 lpFileNames  
 [in] Массив имен файлов необходимо вернуть в неполный локальный путь.  
  
 lpComment  
 [in] Комментарий для применения к каждой из выбранных файлов, возврат. Это `NULL` если подключаемый модуль системы управления версиями следует запрашивать комментарий.  
  
 fOptions  
 [in] Флаги команды, либо 0 или `SCC_KEEP_CHECKEDOUT`.  
  
 pvOptions  
 [in] Параметры, специфичные для подключаемых модулей SCC.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Файлы успешно возвращен.|  
|SCC_E_FILENOTCONTROLLED|Выбранный файл не существует в системе управления версиями.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|  
|SCC_E_NONSPECIFICERROR|Неспецифичную сбоя. Файл не был возвращен.|  
|SCC_E_NOTCHECKEDOUT|Чтобы невозможно было вернуть его файл не извлечен пользователем.|  
|SCC_E_CHECKINCONFLICT|Не удалось выполнить Checkin, так как:<br /><br /> -Другой пользователь вернули вперед и `bAutoReconcile` имел значение false.<br /><br /> -или-<br /><br /> -Автоматическое слияние невозможно (например, когда файлы являются двоичный).|  
|SCC_E_VERIFYMERGE|Файл был автоматическое слияние, но еще не возвращен ожидающие проверка пользователя.|  
|SCC_E_FIXMERGE|Файл был автоматического слияния, но еще не возвращен из-за конфликта слияния, который необходимо разрешить вручную.|  
|SCC_E_NOTAUTHORIZED|Для выполнения этой операции не разрешено пользователю.|  
|SCC_I_OPERATIONCANCELED|Операция была отменена до завершения.|  
|SCC_I_RELOADFILE|Файл или проект должен быть перезагружен.|  
|SCC_E_FILENOTEXIST|Локальный файл не найден.|  
  
## <a name="remarks"></a>Примечания  
 Комментарий применяется ко всем файлам, возврат. Аргумент примечания могут быть `null` строка, в этом случае подключаемый модуль системы управления версиями можно запрашивать у пользователя строка комментария для каждого файла.  
  
 `fOptions` Аргумент можно задать значение `SCC_KEEP_CHECKEDOUT` флаг, указывающий намерения пользователя для возврата файла и снова его извлечь.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
