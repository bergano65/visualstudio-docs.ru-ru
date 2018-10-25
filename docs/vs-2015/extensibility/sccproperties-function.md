---
title: Функция SccProperties | Документация Майкрософт
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
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 020d30c9c81a188e3104928a52e58d7319523338
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914210"
---
# <a name="sccproperties-function"></a>Функция SccProperties
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта функция отображает свойства системы управления версиями для файла или проекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pvContext  
 [in] Структура подключаемого модуля контекста исходного элемента управления.  
  
 hWnd  
 [in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для любой диалоговых окон, которые он предоставляет.  
  
 lpFileName  
 [in] Полное имя файла или проекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Отобразить свойства были успешно.|  
|SCC_I_RELOADFILE|Система управления версиями изменил свойства файла, поэтому интегрированной среды разработки следует перезагрузить этот файл.|  
|SCC_E_PROJNOTOPEN|Указанный проект не был открыт в системе управления версиями.|  
|SCC_E_NOTAUTHORIZED|Пользователь не авторизован для просмотра свойств файла или проекта.|  
|SCC_E_FILENOTCONTROLLED|Указанный файл или проект не в системе управления версиями.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Произошла ошибка неизвестен или Общие.|  
  
## <a name="remarks"></a>Примечания  
 Подключаемый модуль системы управления версиями отображает свойства в собственное диалоговое окно.  
  
 Свойства определяются подключаемый модуль системы управления версиями и может отличаться от подключаемого модуля для подключаемого модуля. Если подключаемый модуль позволяет пользователю изменять свойства системы управления версиями файла, он должен вернуть `SCC_I_RELOAD` сигнала интегрированной среды разработки, необходимо перезагрузить этот файл или проект.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)

