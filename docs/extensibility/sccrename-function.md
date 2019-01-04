---
title: Функция SccRename | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: efd86fcfa728e9dfad05d9feb934bc2b54e5272b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53896140"
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
 [in] Структура подключаемого модуля контекста исходного элемента управления.  
  
 hWnd  
 [in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для любой диалоговых окон, которые он предоставляет.  
  
 lpFileName  
 [in] Полное имя файла имя переименовываемого файла.  
  
 lpNewName  
 [in] Новое полное имя. Если путь к каталогу отличается, затем файл перемещен из одного подкаталога в другой.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
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
 Эта функция позволяет переименовать файл или переместите его из одного расположения в другое в системе управления версиями. Подключаемый модуль системы управления версиями не следует пытаться получить доступ к файлу на диске. IDE отвечает переименовать локальный файл.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)