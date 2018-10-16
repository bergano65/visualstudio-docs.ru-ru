---
title: Команды конструктора | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d46bbe3c9898fae2974b482e1ead607ea486fef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252472"
---
# <a name="command-design"></a>Конструктор команд
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

При добавлении команды VSPackage, необходимо указать которых может отображаться, когда он становится доступен, и способ их обработки.  
  
## <a name="defining-commands"></a>Определение команд  
 Чтобы определить новые команды, включите файл Visual Studio Command Table (.vsct) в проект VSPackage. Если вы создали VSPackage с помощью шаблона пакета Visual Studio, проект содержит один из этих файлов. Дополнительные сведения см. в разделе [Visual Studio Command Table (.Vsct) Files](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio объединяет все файлы .vsct, найденную может отображать его команды. Поскольку эти файлы отличаются от двоичных VSPackage, загрузить пакет, чтобы найти команды имеет Visual Studio. Дополнительные сведения см. в разделе [как пакеты VSPackage добавить элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio использует <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> атрибута регистрации для определения ресурсов меню и команд. Дополнительные сведения см. в разделе [реализации](../../extensibility/internals/command-implementation.md).  
  
 Команды можно изменить во время выполнения в несколько разных способов. Они могут отображаться или скрыты, включить или отключить. Их можно отобразить значки или другим текстовым или содержать разные значения. Большое количество настройки может быть выполнена, прежде чем Visual Studio загружает VSPackage. Дополнительные сведения см. в разделе [как пакеты VSPackage добавить элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Обработчики команд  
 При создании команды необходимо указать обработчик событий, чтобы выполнить команду. Если пользователь выбирает команду, она будет направляться соответствующим образом. Маршрутизации команды означает, что отправляется правильный пакет VSPackage, чтобы включить или отключить его, скрыть или отобразить ее и выполните его, если пользователь выбирает для этого. Дополнительные сведения см. в разделе [маршрутизации алгоритм](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="the-visual-studio-command-environment"></a>Команда среды Visual Studio  
 Visual Studio можно разместить любое количество пакетов VSPackage, а каждый вносить свой вклад в свой собственный набор команд. Среде отображает только команды, которые подходят для текущей задачи. Дополнительные сведения см. в разделе [доступности](../../extensibility/internals/command-availability.md) и [объекты контекста выбора](../../extensibility/internals/selection-context-objects.md).  
  
 Пакет VSPackage, который определяет новые команды, меню, панели инструментов или контекстного меню сведения его команды для Visual Studio во время установки с помощью записи реестра, которые ссылаются на ресурсы в собственных или управляемых сборках. Каждый ресурс, затем ссылается на файл ресурсов (.cto) двоичных данных, создаваемый при компиляции файла Visual Studio Command Table (.vsct). Это позволяет Visual Studio для предоставления наборов объединенных команд, меню и панелей инструментов без необходимости загружать каждого установленного пакета VSPackage.  
  
### <a name="command-organization"></a>Команда организации  
 Среде помещает команды, группы, приоритет и меню.  
  
-   Группы — это логические наборы связанных команд, например, **Вырезать**, **копирования**, и **вставить** группы команд. Группы — это команды, отображаемые в меню.  
  
-   Приоритет определяет порядок, в котором отображаются отдельные команды в группе, в меню.  
  
-   Меню действуют как контейнеры для группы.  
  
 Среде предопределяет некоторые команды, группы и меню. Дополнительные сведения см. в разделе [команды по умолчанию, группы и размещения панели инструментов](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
 Команды могут быть назначены основную группу. Основная группа управляет расположением команды в структуре главного меню и в **Настройка** диалоговое окно. Команда может встречаться в нескольких группах; Например команда может быть в главном меню, в контекстном меню и на панели инструментов. Дополнительные сведения см. в разделе [как пакеты VSPackage добавить элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>маршрутизация команд  
 Процесс маршрутизации команд для пакетов VSPackage и вызова отличается от процесса вызова методов экземпляров объектов.  
  
 Среде направляет команды последовательно из корневого (local) контекста команды, который основывается на текущее выделение, самый внешний контекст (используется глобально). Первый контекст, который способен выполнить команду является тот, который обрабатывает его. Дополнительные сведения см. в разделе [маршрутизации алгоритм](../../extensibility/internals/command-routing-algorithm.md).  
  
 В большинстве случаев среде обрабатывает команды с помощью <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс. Так как схема маршрутизации команд включает множество разные объекты для обработки команд, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> может быть реализован любым количеством объектов; они включают элементы управления Microsoft ActiveX, окно представления реализаций, объекты документа, иерархий проектов и VSPackage сами объекты (для глобальных команд). В некоторых случаях специализированные, например, маршрутизация команд в иерархии, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> интерфейс должен быть реализован.  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Реализация](../../extensibility/internals/command-implementation.md)|В этой статье описывается реализация команд в VSPackage.|  
|[Доступность](../../extensibility/internals/command-availability.md)|Описывается, как Visual Studio контекст определяет, какие команды доступны.|  
|[Алгоритм маршрутизации](../../extensibility/internals/command-routing-algorithm.md)|Описывает, как архитектура маршрутизации команды Visual Studio позволяет команд для обработки в разных пакетов VSPackage.|  
|[Рекомендации по размещению](../../extensibility/internals/command-placement-guidelines.md)|Предлагает методы для позиционирования команд в среде Visual Studio.|  
|[Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Описывает, как пакеты VSPackage могут лучше всего использовать архитектуры команды Visual Studio.|  
|[Стандартное размещение команды, группы и панели инструментов](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Описывает, как пакеты VSPackages могут лучше всего использовать команды, которые включены в Visual Studio.|  
|[Управление пакетами VSPackage](../../extensibility/managing-vspackages.md)|Описывает, как Visual Studio загружает пакеты VSPackage.|  
|[Файлы таблицы команд Visual Studio (VSCT-файлы)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Сведения о файлах vstc на основе XML, которые используются для описания макета и внешнего вида команды в пакеты VSPackage.|

