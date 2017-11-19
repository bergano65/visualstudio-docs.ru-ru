---
title: "Функция SccAdd | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccAdd
helpviewer_keywords: SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8cd55986d7f4597030830906485ba1d7c1b3389
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="sccadd-function"></a>Функция SccAdd
Эта функция добавляет новые файлы системы управления версиями.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pvContext  
 [in] Исходная структура подключаемого модуля контекста элемента управления.  
  
 hWnd  
 [in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для все диалоговые окна, которые он предоставляет.  
  
 nFiles  
 [in] Число файлов, выбранных для добавления в текущий проект, указанный в `lpFileNames` массива.  
  
 lpFileNames  
 [in] Массив полных имен локальных файлов для добавления.  
  
 lpComment  
 [in] Примечание, которое должно быть применено ко всем добавленных файлов.  
  
 pfOptions  
 [in] Массив из командной строки на каждого файла.  
  
 pvOptions  
 [in] Параметры для конкретного подключаемого модуля системы управления версиями.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Добавить операция выполнена успешно.|  
|SCC_E_FILEALREADYEXISTS|Выбранный файл уже существует в системе управления версиями.|  
|SCC_E_TYPENOTSUPPORTED|Тип файла (например, двоичные), системы управления версиями не поддерживается.|  
|SCC_E_OPNOTSUPPORTED|Система управления версиями не поддерживает эту операцию.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|  
|SCC_E_NOTAUTHORIZED|Для выполнения этой операции не разрешено пользователю.|  
|SCC_E_NONSPECIFICERROR|Неспецифичную сбоя; Добавление не выполняется.|  
|SCC_I_OPERATIONCANCELED|Операция отменена до завершения.|  
|SCC_I_RELOADFILE|Файл или проект должен быть перезагружен.|  
|SCC_E_FILENOTEXIST|Локальный файл не найден.|  
  
## <a name="remarks"></a>Примечания  
 Обычные `fOptions` здесь заменяются массивом, `pfOptions`, с одним `LONG` параметр спецификации каждого файла. Это так, как тип файла может изменяться между файлами.  
  
> [!NOTE]
>  Не допускается указывать оба `SCC_FILETYPE_TEXT` и `SCC_FILETYPE_BINARY` параметры для одного файла, но он не указывать ни одного. Установка не совпадает со значением параметра `SCC_FILETYPE_AUTO`, в этом случае система управления подключаемого модуля autodetects тип файлов.  
  
 Ниже приведен список флагов, используемых в `pfOptions` массива:  
  
|Параметр|Значение|Значение|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0x00|Подключаемый модуль системы управления версиями следует определить тип файла.|  
|SCC_FILETYPE_TEXT|0x01|Указывает текстовый файл в кодировке ASCII.|  
|SCC_FILETYPE_BINARY|0x02|Указывает тип файла, отличное от текста ASCII.|  
|SCC_ADD_STORELATEST|0x04|Хранит только последнюю копию файла, без изменения.|  
|SCC_FILETYPE_TEXT_ANSI|0x08|Обрабатывает файл как текст ANSI.|  
|SCC_FILETYPE_UTF8|0x10|Обрабатывает файл как текст в кодировке Юникод в формате UTF-8.|  
|SCC_FILETYPE_UTF16LE|0x20|Обрабатывает файл как текст в кодировке Юникод в UTF16 формате с прямым порядком байтов.|  
|SCC_FILETYPE_UTF16BE|0x40|Обрабатывает файл как текст в кодировке Юникод UTF16 Big Endian в формате.|  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)