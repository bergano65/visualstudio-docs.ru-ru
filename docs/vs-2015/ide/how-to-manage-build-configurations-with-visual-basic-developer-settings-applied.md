---
title: Практическое руководство. Управление конфигурациями построений с применением параметров разработчика Visual Basic | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c2cf949803bcc864937e67c1f94addaaf6abacbd
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685641"
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>Практическое руководство. Управление конфигурациями построений с применением параметров разработчика Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

По умолчанию все расширенные параметры сборки скрыты при применении параметров разработчика [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. В этом разделе объясняется, как вручную включить эти параметры.  
  
## <a name="enabling-advanced-build-configurations"></a>Включение дополнительных конфигураций сборки  
 По умолчанию в параметрах разработчика [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] возможность открыть диалоговое окно **диспетчера конфигураций**, как и списки **конфигураций** и **платформ** в [конструкторе проектов](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7), скрыта.  
  
#### <a name="to-enable-advanced-build-configurations"></a>Включение дополнительных конфигураций сборок  
  
1. В меню **Сервис** выберите пункт **Параметры**.  
  
2. Разверните узел **Проекты и решения** и выберите **Общие**.  
  
    > [!NOTE]
    > Узел **Общие** отображается, даже если не установлен флажок **Показать все параметры**. Если вы хотите просмотреть все доступные параметры, щелкните **Показать все параметры**.  
  
3. Установите флажок **Показывать дополнительные конфигурации построения**.  
  
4. Нажмите кнопку **ОК**.  
  
     Теперь в меню **Сборка** можно выбрать **Диспетчер конфигурации**, а списки **конфигураций** и **платформ** отображаются в конструкторе проектов.  
  
## <a name="see-also"></a>См. также раздел  
 [Общие сведения о конфигурациях построения](../ide/understanding-build-configurations.md)   
 [Компилирование и сборка](../ide/compiling-and-building-in-visual-studio.md)
