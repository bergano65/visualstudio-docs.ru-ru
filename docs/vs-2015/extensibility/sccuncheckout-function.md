---
title: Функция SccUncheckout | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b74e4c2ebc672af11133c0afd1237cc27169ca6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568729"
---
# <a name="sccuncheckout-function"></a>Функция SccUncheckout
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [функция SccUncheckout](https://docs.microsoft.com/visualstudio/extensibility/sccuncheckout-function).  
  
Эта функция отменяет предыдущей операции извлечения, благодаря чему восстанавливается содержимое выбранного файла или файлов в состояние до извлечения. Все изменения, внесенные в файл с момента извлечения будут утеряны.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 [in] Структура подключаемого модуля контекста исходного элемента управления.  
  
 hWnd  
 [in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для любой диалоговых окон, которые он предоставляет.  
  
 nFiles  
 [in] Число файлов, указанных в `lpFileNames` массива.  
  
 lpFileNames  
 [in] Массив имен файлов, для которого нужно отменить извлечение полный локальный путь.  
  
 Возможности  
 [in] Команда флаги (не используется).  
  
 pvOptions  
 [in] Параметры конкретного подключаемого модуля системы управления версиями.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Операция отмены извлечения успешно.|  
|SCC_E_FILENOTCONTROLLED|Выбранный файл не существует в системе управления версиями.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|  
|SCC_E_NONSPECIFICERROR|Обнаружена неспецифическая ошибка. Отменить извлечение завершилась неудачно.|  
|SCC_E_NOTCHECKEDOUT|Пользователь не имеет извлеченный файл.|  
|SCC_E_NOTAUTHORIZED|Пользователю запрещено для этой операции.|  
|SCC_E_PROJNOTOPEN|Проект не был открыт из системы управления версиями.|  
|SCC_I_OPERATIONCANCELED|Операция была отменена до завершения.|  
  
## <a name="remarks"></a>Примечания  
 После выполнения этой операции `SCC_STATUS_CHECKEDOUT` и `SCC_STATUS_MODIFIED` флаги оба очищается файлы, на которых была выполнена операция отмены извлечения.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)

