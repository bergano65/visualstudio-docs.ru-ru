---
title: Устранение неполадок расширений для схем слоев | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: troubleshooting
helpviewer_keywords:
- layer diagrams, extension errors
- layer diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dd4560673259373b68b370e73a43de424fb7bdb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658475"
---
# <a name="troubleshoot-extensions-for-layer-diagrams"></a>Устранение неполадок, связанных с расширениями для схем слоев
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе рассматриваются некоторые проблемы, которые могут возникнуть при создании расширений модели слоев.

#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-layer-diagrams-in-the-experimental-instance-of-vsprvs"></a>При нажатии клавиши F5 для отладки расширения команды, обработчики жестов, расширения проверки или пользовательские свойства не отображаются на схемах слоев в экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

1. Откройте решение расширения в экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и в меню **Сборка** выберите **Перестроить решение**.

2. Нажмите клавишу **F5** или **CTRL + F5** , чтобы запустить экспериментальный экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Откройте схему слоев и протестируйте расширение.

   При необходимости выполните описанную ниже процедуру.

#### <a name="an-old-version-of-my-extension-runs"></a>Запускается старая версия расширения.

1. Убедитесь в том, что не выполняется экспериментальный экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

2. Удалите следующую папку:%Локалаппдата%\микрософт\висуалстудио \\ [версия] \компонентмоделкаче

   > [!NOTE]
   > % LocalAppData% обычно *DriveName*: \Users \\ *username*\аппдата\локал.

   При необходимости выполните описанную ниже процедуру.

#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Отображается старая версия результатов проверки, либо не вызывается метод проверки.

1. В экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] в меню **Сборка** выберите **Очистить решение**. Она позволяет очистить кэшированные результаты предыдущего анализа проверки.

2. Убедитесь в том, что слои в модели связаны с элементами кода и что в модели есть хотя бы одна связь зависимости. Проверка не вызывается, если нет элементов для проверки.

3. Стандартные точки останова могут не работать в методе проверки, так как он выполняется в отдельном процессе. Для пошагового выполнения метода нужно вставить вызов метода `System.Diagnostics.Debugger.Launch()`.

4. В разделе **source. extension. vsixmanifest** проекта проверки слоев убедитесь, что в поле **содержимое**добавлены элемент **компонента MEF** и **Пользовательский элемент типа расширения** .

## <a name="see-also"></a>См. также:
 [Расширение схем слоев](../modeling/extend-layer-diagrams.md)
