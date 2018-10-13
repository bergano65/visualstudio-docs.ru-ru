---
title: Практическое руководство. Управление конфигурациями построений с применением параметров разработчика Visual Basic | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio, building with Visual Basic settings
- MSBuild, debug build
- advanced build configurations
- building with Visual Basic developer settings
- debug builds
- MSBuild, release build
- release builds
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b191b5d4223d32e4d620c779f5813c0db651a6cc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49300564"
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>Практическое руководство. Управление конфигурациями построений с применением параметров разработчика Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

По умолчанию все расширенные параметры сборки скрыты при применении параметров разработчика [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. В этом разделе объясняется, как вручную включить эти параметры.  
  
## <a name="enabling-advanced-build-configurations"></a>Включение дополнительных конфигураций сборки  
 По умолчанию в параметрах разработчика [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] возможность открыть диалоговое окно **диспетчера конфигураций**, как и списки **конфигураций** и **платформ** в [конструкторе проектов](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7), скрыта.  
  
#### <a name="to-enable-advanced-build-configurations"></a>Включение дополнительных конфигураций сборок  
  
1.  В меню **Сервис** выберите пункт **Параметры**.  
  
2.  Разверните узел **Проекты и решения** и выберите **Общие**.  
  
    > [!NOTE]
    >  Узел **Общие** отображается, даже если не установлен флажок **Показать все параметры**. Если вы хотите просмотреть все доступные параметры, щелкните **Показать все параметры**.  
  
3.  Установите флажок **Показывать дополнительные конфигурации построения**.  
  
4.  Нажмите кнопку **ОК**.  
  
     Теперь в меню **Сборка** можно выбрать **Диспетчер конфигурации**, а списки **конфигураций** и **платформ** отображаются в конструкторе проектов.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о конфигурациях построения](../ide/understanding-build-configurations.md)   
 [Компилирование и сборка](../ide/compiling-and-building-in-visual-studio.md)



