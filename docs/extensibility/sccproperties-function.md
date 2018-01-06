---
title: "Функция SccProperties | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccProperties
helpviewer_keywords: SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: efaa2877743fcf69a61a79633108d203442489e0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="sccproperties-function"></a>Функция SccProperties
Эта функция отображает свойства системы управления версиями для файла или проекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pvContext  
 [in] Исходная структура подключаемого модуля контекста элемента управления.  
  
 hWnd  
 [in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для все диалоговые окна, которые он предоставляет.  
  
 lpFileName  
 [in] Полное имя файла или проекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Успешно отобразить свойства.|  
|SCC_I_RELOADFILE|Системы управления версиями изменил свойства файла, поэтому интегрированной среды разработки следует перезагрузить этот файл.|  
|SCC_E_PROJNOTOPEN|Указанный проект не был открыт в системе управления версиями.|  
|SCC_E_NOTAUTHORIZED|Пользователь не авторизован для просмотра свойств файла или проекта.|  
|SCC_E_FILENOTCONTROLLED|Указанный файл или проект не находится в системе управления версиями.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Произошла ошибка неизвестен или Общие.|  
  
## <a name="remarks"></a>Примечания  
 Подключаемый модуль системы управления версиями отображаются свойства в диалоговом окне свои собственные.  
  
 Свойства определяются подключаемый модуль системы управления версиями и может отличаться от подключаемого модуля для подключаемого модуля. Если подключаемый модуль позволяет пользователю изменять свойства элемента управления исходного файла, он должен возвращать `SCC_I_RELOAD` сигнала интегрированной среды разработки, необходимо перезагрузить этот файл или проект.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)