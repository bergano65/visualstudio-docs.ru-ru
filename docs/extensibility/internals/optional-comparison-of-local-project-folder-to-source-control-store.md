---
title: "Сравнение папки проекта в системе управления версиями | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: b2ed6955e5ba6fa334cc89a0c2ea8a3d4248f362
ms.lasthandoff: 02/22/2017

---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Необязательные сравнения папки локального проекта в системе управления версиями
В источнике управления Plug-in API 1.2 сравнение папку локального проекта и системы управления версиями осуществляется с помощью функции [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) и [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 В **обозревателе решений**, если папка выбрана вместо отдельного файла, **сравнения версий** контекстное меню вызывает новый [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) и [SccDirDiff](../../extensibility/sccdirdiff-function.md) в подключаемый модуль системы управления версиями.  
  
## <a name="new-capability-flags"></a>Флаги новых возможностей  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Новые функции  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 `SccDirQueryInfo` Функция вызывается перед `SccDirDiff` определить рабочий каталог в системе управления версиями. `SccDirDiff` Функция отображает различия между текущей локальной папки и соответствующие папки системы управления версиями. Эта команда запрашивает подключаемого модуля, чтобы отобразить список изменений в каталог системы управления версиями. Подключаемый модуль системы управления версиями предоставляет свой собственный пользовательский Интерфейс для отображения различий.  
  
> [!NOTE]
>  Эта функция использует те же флаги команды, как [SccDiff](../../extensibility/sccdiff-function.md). Как подключаемый поставщик управления версиями вы можете не поддерживают операции «быстрое diff» для каталогов.  
  
## <a name="see-also"></a>См. также  
 [Новые возможности в подключаемый модуль API версия системы управления версиями 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
