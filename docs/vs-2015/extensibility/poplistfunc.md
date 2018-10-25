---
title: POPLISTFUNC | Документация Майкрософт
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
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bfa528edb20851456926ee939cef86730eeedfe3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941975"
---
# <a name="poplistfunc"></a>POPLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Этот обратный вызов передается [SccPopulateList](../extensibility/sccpopulatelist-function.md) Интегрированной средой разработки и используется подключаемый модуль системы управления версиями, чтобы обновить список файлов или каталогов (также указан для `SccPopulateList` функции).  
  
 Когда пользователь выбирает **получить** команды в интегрированной среде разработки, среда интегрированной разработки отобразит список всех файлов, которые пользователь может получить. К сожалению интегрированной среды разработки не знает точный список всех файлов, которые пользователь может получить; только подключаемый модуль имеет этот список. Если другим пользователям добавления файлов в проект элемента управления исходного кода, эти файлы должны появиться в списке, но интегрированной среды разработки не знает о них. IDE формирует список файлов, которые он считает, что пользователь может получить. Прежде чем он отображает этот список для пользователя, он вызывает [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` предоставляя подключаемый модуль системы управления версиями возможность добавлять и удалять файлы из списка.  
  
## <a name="signature"></a>Подпись  
 Подключаемый модуль системы управления версиями изменяет список путем вызова функции, реализуемые интегрированной среды разработки со следующим прототипом:  
  
```cpp#  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>Параметры  
 pvCallerData  
 `pvCallerData` Параметр, передаваемый в вызывающем объекте (IDE) [SccPopulateList](../extensibility/sccpopulatelist-function.md). Подключаемый модуль системы управления версиями следует предполагать только то содержимое этого параметра.  
  
 fAddRemove  
 Если `TRUE`, `lpFileName` — это файл, который должен быть добавлен в список файлов. Если `FALSE`, `lpFileName` — это файл, который должен быть удален из списка файлов.  
  
 nStatus  
 Состояние `lpFileName` (сочетание `SCC_STATUS` битов; см. описание [код состояния файла](../extensibility/file-status-code-enumerator.md) сведения).  
  
 lpFileName  
 Полный путь к каталогу имя файла, чтобы добавить или удалить из списка.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
|Значение|Описание|  
|-----------|-----------------|  
|`TRUE`|Подключаемый модуль можно продолжить вызов этой функции.|  
|`FALSE`|Возникла проблема со стороны интегрированной среды разработки (например, из-за нехватки памяти). Подключаемый модуль должен остановить операцию.|  
  
## <a name="remarks"></a>Примечания  
 Для каждого файла, подключаемый модуль системы управления версиями, которые требуется добавить или удалить из списка файлов, он вызывает эту функцию, передавая `lpFileName`. `fAddRemove` Флаг указывает, новый файл для добавления в список или удалить старый файл. `nStatus` Дает состояние файла. После завершения добавления и удаления файлов подключаемого модуля SCC, она возвращает [SccPopulateList](../extensibility/sccpopulatelist-function.md) вызова.  
  
> [!NOTE]
>  `SCC_CAP_POPULATELIST` Бит функции является обязательным для Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Функции обратного вызова, реализованные интегрированной среды разработки](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Подключаемых модулей системы управления версиями](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Код состояния файла](../extensibility/file-status-code-enumerator.md)

