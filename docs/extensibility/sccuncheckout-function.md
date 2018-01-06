---
title: "Функция SccUncheckout | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccUncheckout
helpviewer_keywords: SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f9b4b2f06b8ee020ca07e780836ec2abbbc96e82
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="sccuncheckout-function"></a>Функция SccUncheckout
Эта функция отменяет предыдущей операции извлечения, благодаря чему восстанавливается содержимое выбранного файла или файлов в состояние до извлечения. Все изменения, внесенные в файл после такого извлечения, будут утеряны.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
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
 [in] Массив имен файлов, для которых Отмена извлечения неполный локальный путь.  
  
 fOptions  
 [in] Команда флаги (не используется).  
  
 pvOptions  
 [in] Параметры для конкретного подключаемого модуля системы управления версиями.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Отмена извлечения прошла успешно.|  
|SCC_E_FILENOTCONTROLLED|Выбранный файл не существует в системе управления версиями.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|  
|SCC_E_NONSPECIFICERROR|Неспецифичную сбоя. Отмена извлечения завершилась неуспешно.|  
|SCC_E_NOTCHECKEDOUT|Пользователь не имеет файл извлечен.|  
|SCC_E_NOTAUTHORIZED|Для выполнения этой операции не разрешено пользователю.|  
|SCC_E_PROJNOTOPEN|Проект не был открыт из системы управления версиями.|  
|SCC_I_OPERATIONCANCELED|Операция отменена до завершения.|  
  
## <a name="remarks"></a>Примечания  
 После выполнения этой операции `SCC_STATUS_CHECKEDOUT` и `SCC_STATUS_MODIFIED` флаги оба очищается файлы, на которых была выполнена операция отмены извлечения.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)