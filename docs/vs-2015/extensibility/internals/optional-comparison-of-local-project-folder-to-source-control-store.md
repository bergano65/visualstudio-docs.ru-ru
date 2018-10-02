---
title: Необязательное сравнение папки локального проекта Store управления источника | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b6806a01127250b2376fee0aa77d55554eeba9bc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570145"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Необязательное сравнение папки локального проекта с системой управления версиями
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [сравнить папки проекта, для управления Store источника](https://docs.microsoft.com/visualstudio/extensibility/internals/optional-comparison-of-local-project-folder-to-source-control-store).  
  
В источнике управления 1.2 API подключаемых модулей, сравнение между локальной папке проекта и система управления версиями осуществляется с помощью функции [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) и [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 В рамках **обозревателе решений**, если папка выбрана вместо отдельного файла, **сравнить версии** контекстное меню вызывает новый [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) и [ SccDirDiff](../../extensibility/sccdirdiff-function.md) подключаемый модуль системы управления версиями.  
  
## <a name="new-capability-flags"></a>Новые флаги возможностей  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Новые функции  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 `SccDirQueryInfo` Функция вызывается перед `SccDirDiff` чтобы определить рабочий каталог, контролируемого системой управления версиями. `SccDirDiff` Функция отображает различия между текущий локальный каталог и соответствующие папки системы управления версиями. Эта команда запрашивает у системы управления версиями, подключаемый модуль, чтобы отобразить список изменений в каталог. Подключаемый модуль системы управления версиями предоставляет свой собственный пользовательский Интерфейс для отображения различий.  
  
> [!NOTE]
>  Эта функция использует те же флаги команды, как [SccDiff](../../extensibility/sccdiff-function.md). Как подключаемый модуль поставщика управления версиями вы можете не поддерживают «быстрые операции инструмента сравнения» для каталогов.  
  
## <a name="see-also"></a>См. также  
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

