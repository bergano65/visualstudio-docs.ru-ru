---
title: "Функция SccRemove | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccRemove
helpviewer_keywords: SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5f4d7d76e80fa165206a3faa53835b74c2716d94
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="sccremove-function"></a>Функция SccRemove
Эта функция удаляет файлы из системы управления версиями.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccRemove(  
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
 [in] Число файлов, указанных в `lpFileNames` массива.  
  
 lpFileNames  
 [in] Массив имен файлов для удаления неполный локальный путь.  
  
 lpComment  
 [in] Примечание, которое должно применяться к каждому файлу удаления.  
  
 fOptions  
 [in] Команда флаги (неиспользуемого).  
  
 pvOptions  
 [in] Параметры для конкретного подключаемого модуля системы управления версиями.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Удаление выполнено успешно.|  
|SCC_E_FILENOTCONTROLLED|Выбранный файл не существует в системе управления версиями.|  
|SCC_E_OPNOTSUPPORTED|Система управления версиями не поддерживает эту операцию.|  
|SCC_E_ISCHECKEDOUT|Не удается удалить файл, поскольку он извлечен в настоящее время у пользователя.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов.|  
|SCC_E_NOTAUTHORIZED|Для выполнения этой операции не разрешено пользователю.|  
|SCC_E_NONSPECIFICERROR|Неспецифичную сбоя; файл не был удален.|  
|SCC_I_OPERATIONCANCELED|Операция отменена до завершения.|  
  
## <a name="remarks"></a>Примечания  
 Эта функция удаляет файлы из системы управления версиями, но они не удаляются с локального жесткого диска пользователя.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)