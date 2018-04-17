---
title: Сравнение папки проекта в системе управления версиями | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e0f6f2185385ee7ec3942556a43f58d43e7a4da
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Необязательный сравнения папке локального проекта в системе управления версиями
В источнике управления 1.2 API подключаемых модулей, сравнение папки локального проекта и системы управления версиями осуществляется с помощью функции [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) и [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 В пределах **обозревателе решений**, если папка выбрана вместо отдельного файла, **сравнить версии** контекстное меню вызывает новый [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) и [ SccDirDiff](../../extensibility/sccdirdiff-function.md) в подключаемый модуль системы управления версиями.  
  
## <a name="new-capability-flags"></a>Флаги новых возможностей  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Новые функции  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 `SccDirQueryInfo` Функция вызывается перед `SccDirDiff` чтобы определить рабочий каталог, контролируемого системой управления версиями. `SccDirDiff` Функция отображает различия между текущей локальной папки и соответствующей папкой системы управления версиями. Эта команда запрашивает подключаемого модуля, чтобы отобразить список изменений в папку системы управления версиями. Подключаемый модуль системы управления версиями предоставляет собственный пользовательский Интерфейс для отображения различий.  
  
> [!NOTE]
>  Эта функция использует те же флаги команды, как [SccDiff](../../extensibility/sccdiff-function.md). Как подключаемый модуль поставщик системы управления версиями вы можете не поддерживает операции «быстрый diff» для каталогов.  
  
## <a name="see-also"></a>См. также  
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)