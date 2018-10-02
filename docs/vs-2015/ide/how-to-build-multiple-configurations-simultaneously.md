---
title: Практическое руководство. Сборка с использованием нескольких конфигураций | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bca6142edff2eea293db50f0af9b8f86a4fc47dd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558697"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Практическое руководство. Построение с использованием нескольких конфигураций
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: создавать одновременно несколько конфигураций](https://docs.microsoft.com/visualstudio/ide/how-to-build-multiple-configurations-simultaneously).  
  
Большинство типов проектов можно создать с использованием нескольких или даже всех конфигураций сборки одновременно с помощью диалогового окна **Пакетная сборка**. Однако вы не можете одновременно выполнять сборку следующих типов проектов в нескольких конфигурациях сборок:  
  
1.  Приложения [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], созданные для Windows с использованием JavaScript.  
  
2.  Все проекты Visual Basic.  
  
 Дополнительные сведения о конфигурациях сборки см. в разделе [Общие сведения о конфигурациях сборки](../ide/understanding-build-configurations.md).  
  
### <a name="to-build-a-project-in-multiple-build-configurations"></a>Сборка проекта в нескольких конфигурациях сборок  
  
1.  В строке меню выберите **Сборка** и **Пакетная сборка**.  
  
2.  В столбце **Сборка** установите флажки для конфигураций, с которыми требуется выполнить сборку проекта.  
  
    > [!TIP]
    >  Если вы хотите изменить или создать конфигурацию сборки для решения, выберите **Сборка**, **Диспетчер конфигураций** в строке меню, чтобы открыть диалоговое окно **Диспетчер конфигураций**. После изменения конфигурации сборки для решения нажмите кнопку **Пересобрать** в диалоговом окне **Пакетная сборка**, чтобы обновить все конфигурации сборки для проектов в решении.  
  
3.  Нажмите кнопку **Сборка** или **Пересобрать** для сборки проекта с указанными конфигурациями.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Создание и изменение конфигураций](../ide/how-to-create-and-edit-configurations.md)   
 [Общие сведения о конфигурациях построения](../ide/understanding-build-configurations.md)   
 [Параллельная сборка нескольких проектов](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)



