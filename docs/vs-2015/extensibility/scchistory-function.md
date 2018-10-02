---
title: Функция SccHistory | Документация Майкрософт
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
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f3a01e3d854b2527a38595509699aa94a222a9ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571145"
---
# <a name="scchistory-function"></a>Функция SccHistory
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [функция SccHistory](https://docs.microsoft.com/visualstudio/extensibility/scchistory-function).  
  
Эта функция отображает журнал указанных файлов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pvContext`  
 [in] Структура подключаемого модуля контекста исходного элемента управления.  
  
 `hWnd`  
 [in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для любой диалоговых окон, которые он предоставляет.  
  
 `nFiles`  
 [in] Число файлов, указанных в `lpFileName` массива.  
  
 `lpFileName`  
 [in] Массив полных имен файлов.  
  
 `fOptions`  
 [in] Команда флаги (в настоящее время не используется).  
  
 `pvOptions`  
 [in] Параметры конкретного подключаемого модуля системы управления версиями.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Журнал версий был успешно получен.|  
|SCC_I_RELOADFILE|Система управления версиями фактически изменения файла на диске при получении журнала (например, путем получения более старые версии), поэтому интегрированной среды разработки следует перезагрузить этот файл.|  
|SCC_E_FILENOTCONTROLLED|Файл не существует в системе управления версиями.|  
|SCC_E_OPNOTSUPPORTED|Система управления версиями не поддерживает эту операцию.|  
|SCC_E_NOTAUTHORIZED|Пользователю запрещено для этой операции.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|  
|SCC_E_PROJNOTOPEN|Проект не был открыт.|  
|SCC_E_NONSPECIFICERROR|Обнаружена неспецифическая ошибка. Не удалось получить файл журнала.|  
  
## <a name="remarks"></a>Примечания  
 Подключаемый модуль системы управления версиями можно отобразить собственное диалоговое окно, чтобы отобразился журнал каждого файла с помощью `hWnd` как родительское окно. Кроме того, необязательный текст вывода обратного вызова функции передан [SccOpenProject](../extensibility/sccopenproject-function.md) можно использовать, если он поддерживается.  
  
 Обратите внимание, что при определенных обстоятельствах, анализируемый файл может измениться во время выполнения этого вызова. Например [!INCLUDE[vsvss](../includes/vsvss-md.md)] команда history дает пользователю возможность получить старую версию файла. В этом случае система управления подключаемый модуль возвращает `SCC_I_RELOAD` предупреждения интегрированной среды разработки, что необходимо перезагрузить файл.  
  
> [!NOTE]
>  Если подключаемый модуль системы управления версиями не поддерживает эту функцию для массива файлов, могут отображаться только данные файла журнала для первого файла.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)

