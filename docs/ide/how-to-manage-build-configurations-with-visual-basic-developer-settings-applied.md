---
title: Практическое руководство. Управление конфигурациями сборок с применением параметров разработчика Visual Basic | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, building with Visual Basic settings
- MSBuild, debug build
- advanced build configurations
- building with Visual Basic developer settings
- debug builds
- MSBuild, release build
- release builds
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 954a968de9840e6f23c3e8ff5ab0ff4d0fa761cb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>Практическое руководство. Управление конфигурациями сборок с применением параметров разработчика Visual Basic
По умолчанию все расширенные параметры сборки скрыты при применении параметров разработчика [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. В этом разделе объясняется, как вручную включить эти параметры.  
  
## <a name="enable-advanced-build-configurations"></a>Включение дополнительных конфигураций сборок  
 По умолчанию в параметрах разработчика [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] возможность открыть диалоговое окно **диспетчера конфигураций**, как и списки **конфигураций** и **платформ** в [конструкторе проектов](..//ide/reference/application-page-project-designer-visual-basic.md), скрыта.  
  
#### <a name="to-enable-advanced-build-configurations"></a>Включение дополнительных конфигураций сборок  
  
1.  В меню **Сервис** выберите пункт **Параметры**.  
  
2.  Разверните узел **Проекты и решения** и выберите **Общие**.  
  
    > [!NOTE]
    >  Узел **Общие** отображается, даже если не установлен флажок **Показать все параметры**. Если вы хотите просмотреть все доступные параметры, щелкните **Показать все параметры**.  
  
3.  Установите флажок **Показывать дополнительные конфигурации построения**.  
  
4.  Нажмите кнопку **ОК**.  
  
     Теперь в меню **Сборка** можно выбрать пункт **Диспетчер конфигурации**, а списки **конфигураций** и **платформ** отображаются в **конструкторе проектов**.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о конфигурациях сборок](../ide/understanding-build-configurations.md)   
 [Компиляция и сборка](../ide/compiling-and-building-in-visual-studio.md)