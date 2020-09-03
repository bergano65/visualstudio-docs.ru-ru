---
title: Практическое руководство. Сборка с использованием нескольких конфигураций | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 719b31e834b5410dd137a0c5b69cc07ae01651e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645472"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Практическое руководство. Построение с использованием нескольких конфигураций
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Большинство типов проектов можно создать с использованием нескольких или даже всех конфигураций сборки одновременно с помощью диалогового окна **Пакетная сборка**. Однако вы не можете одновременно выполнять сборку следующих типов проектов в нескольких конфигурациях сборок:

1. Приложения [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], созданные для Windows с использованием JavaScript.

2. Все проекты Visual Basic.

   Дополнительные сведения о конфигурациях сборки см. в разделе [Основные сведения о конфигурациях сборки](../ide/understanding-build-configurations.md).

### <a name="to-build-a-project-in-multiple-build-configurations"></a>Сборка проекта в нескольких конфигурациях сборок

1. В строке меню выберите **Сборка** и **Пакетная сборка**.

2. В столбце **Сборка** установите флажки для конфигураций, с которыми требуется выполнить сборку проекта.

    > [!TIP]
    > Если вы хотите изменить или создать конфигурацию сборки для решения, выберите **Сборка**, **Диспетчер конфигураций** в строке меню, чтобы открыть диалоговое окно **Диспетчер конфигураций**. После изменения конфигурации сборки для решения нажмите кнопку **Пересобрать** в диалоговом окне **Пакетная сборка**, чтобы обновить все конфигурации сборки для проектов в решении.

3. Нажмите кнопку **Сборка** или **Пересобрать** для сборки проекта с указанными конфигурациями.

## <a name="see-also"></a>См. также:
 [Как создавать и изменять конфигурации](../ide/how-to-create-and-edit-configurations.md) [Общие сведения о конфигурациях сборки](../ide/understanding-build-configurations.md) , [создающих несколько проектов в параллельном](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) режиме
