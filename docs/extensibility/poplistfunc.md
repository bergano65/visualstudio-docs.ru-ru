---
title: "POPLISTFUNC | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: POPDIRLISTFUNC
helpviewer_keywords: POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dc15af65c6541df5ef77a3bdc85ee0e59fa20991
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="poplistfunc"></a>POPLISTFUNC
Этот обратный вызов передается [SccPopulateList](../extensibility/sccpopulatelist-function.md) в интегрированной среде разработки и используется подключаемый модуль системы управления версиями, чтобы обновить список файлов или каталогов (также указан для `SccPopulateList` функции).  
  
 Когда пользователь выбирает **получить** команды в IDE, интегрированная среда разработки отображает список всех файлов, которые пользователь может получить. К сожалению интегрированной среды разработки не знает точный список всех файлов, которые пользователь может получить; только подключаемый модуль имеет этот список. Если другим пользователям добавления файлов в проект элемента управления исходного кода, эти файлы должны отображаться в списке, но интегрированной среды разработки не знает о них. IDE создает список файлов, которые он полагает, что пользователь может получить. Перед отображением этого списка для пользователя, он вызывает [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` предоставление подключаемый модуль системы управления версиями возможность добавлять и удалять файлы из списка.  
  
## <a name="signature"></a>Подпись  
 Подключаемый модуль системы управления версиями изменяет список путем вызова функции реализованы в интегрированной среде разработки с следующий прототип:  
  
```cpp  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>Параметры  
 pvCallerData  
 `pvCallerData` Параметр, передаваемый в вызывающем объекте (IDE) [SccPopulateList](../extensibility/sccpopulatelist-function.md). Подключаемый модуль системы управления версиями следует предполагать о содержимом этого параметра.  
  
 fAddRemove  
 Если `TRUE`, `lpFileName` — это файл, который должен быть добавлен в список файлов. Если `FALSE`, `lpFileName` — файл, который должен быть удален из списка файлов.  
  
 nStatus  
 Состояние `lpFileName` (сочетание `SCC_STATUS` bits см. в разделе [код состояния файла](../extensibility/file-status-code-enumerator.md) подробные сведения).  
  
 lpFileName  
 Полный путь к каталогу имени файла, чтобы добавить или удалить из списка.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`TRUE`|Подключаемый модуль можно продолжить вызов этой функции.|  
|`FALSE`|Возникла проблема со стороны интегрированной среды разработки (например, нехватки памяти). Подключаемый модуль должен остановить операцию.|  
  
## <a name="remarks"></a>Примечания  
 Для каждого файла, подключаемый модуль системы управления версиями требуется добавить или удалить из списка, он вызывает эту функцию, передавая `lpFileName`. `fAddRemove` Флаг указывает новый файл, чтобы добавить в список или удалить старый файл. `nStatus` Указывает состояние файла. После завершения добавления и удаления файлов подключаемого модуля SCC, она возвращает [SccPopulateList](../extensibility/sccpopulatelist-function.md) вызова.  
  
> [!NOTE]
>  `SCC_CAP_POPULATELIST` Бит функции не требуется для Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Функции обратного вызова, реализуемый интегрированной среды разработки](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Подключаемые модули управления версиями](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Код состояния файла](../extensibility/file-status-code-enumerator.md)