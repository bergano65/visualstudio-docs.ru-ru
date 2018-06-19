---
title: Функция SccRename | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c24d84ff659d287f3b32be2b5585ded16b148395
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137808"
---
# <a name="sccrename-function"></a>Функция SccRename
Эта функция переименовывает файл в системе управления версиями.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pvContext  
 [in] Исходная структура подключаемого модуля контекста элемента управления.  
  
 hWnd  
 [in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для все диалоговые окна, которые он предоставляет.  
  
 lpFileName  
 [in] Имя переименовываемого файла полным путем к файлу.  
  
 lpNewName  
 [in] Полное имя нового. Если путь к каталогу не совпадают, файл перемещен в из одной папки в другую.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Операция переименования завершена успешно.|  
|SCC_E_PROJNOTOPEN|Проект не открыт в системе управления версиями.|  
|SCC_E_FILENOTCONTROLLED|Файл не существует в системе управления версиями.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов.|  
|SCC_E_NOTAUTHORIZED|Пользователь не авторизован для выполнения этой операции.|  
|SCC_E_COULDNOTCREATEPROJECT|Не удалось создать проект в рамках процесса переименования.|  
|SCC_E_OPNOTPERFORMED|Операция не выполнена.|  
|SCC_E_NONSPECIFICERROR|Произошла ошибка не задано или Общие.|  
  
## <a name="remarks"></a>Примечания  
 Эта функция используется для того, чтобы переименовать файл или переместите его из одного расположения в другое в системе управления версиями. Подключаемый модуль системы управления версиями не следует пытаться получить доступ к файлу на диске. Интегрированная среда разработки возлагается переименовать локальный файл.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)