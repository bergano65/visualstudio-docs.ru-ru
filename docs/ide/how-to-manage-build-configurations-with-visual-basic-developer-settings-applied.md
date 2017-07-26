---
title: "Практическое руководство. Управление конфигурациями построений с применением параметров разработчика Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
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
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 782d860d94cd9e7d4967076a5ea0d3fe86b29400
ms.contentlocale: ru-ru
ms.lasthandoff: 05/24/2017

---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>Практическое руководство. Управление конфигурациями построений с применением параметров разработчика Visual Basic
По умолчанию все расширенные параметры сборки скрыты при применении параметров разработчика [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. В этом разделе объясняется, как вручную включить эти параметры.  
  
## <a name="enabling-advanced-build-configurations"></a>Включение дополнительных конфигураций сборки  
 По умолчанию в параметрах разработчика [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] возможность открыть диалоговое окно **диспетчера конфигураций**, как и списки **конфигураций** и **платформ** в [конструкторе проектов](..//ide/reference/application-page-project-designer-visual-basic.md), скрыта.  
  
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
