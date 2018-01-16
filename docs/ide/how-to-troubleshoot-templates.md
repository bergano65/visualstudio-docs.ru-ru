---
title: "Устранение неполадок, связанных с загрузкой шаблона проекта и шаблона элемента Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ba6d9a73cd45a0e497fb2ecc0f4b4697071e3b37
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-troubleshoot-templates"></a>Практическое руководство. Устранение неполадок, связанных с шаблонами

Если шаблон не загружается в среде разработки, локализовать проблему можно несколькими способами.

## <a name="validate-the-vstemplate-file"></a>Проверка файла VSTEMPLATE

Если файл VSTEMPLATE в шаблоне не соответствует схеме шаблона Visual Studio, шаблон может не отображаться в диалоговом окне **Новый проект**.

### <a name="to-validate-the-vstemplate-file"></a>Процедура проверки файла VSTEMPLATE

1. Найдите ZIP-файл, содержащий шаблон.

1. Извлеките ZIP-файл.

1. В Visual Studio в меню **Файл** выберите **Открыть** > **Файл**.

1. Выберите файл VSTEMPLATE для шаблона и нажмите кнопку **Открыть**.

1. Убедитесь, что XML-код в файле VSTEMPLATE соответствует схеме шаблона. Дополнительные сведения о схеме VSTEMPLATE см. в разделе [Справочник по схеме шаблонов](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Чтобы обеспечить поддержку IntelliSense во время работы с файлом VSTEMPLATE, добавьте атрибут `xmlns` в элемент `VSTemplate` и присвойте ему значение http://schemas.microsoft.com/developer/vstemplate/2005.

1. Сохраните VSTEMPLATE-файл и закройте его.

1. Выберите включенные в шаблон файлы, щелкните правой кнопкой мыши и выберите пункты **Отправить** > **Сжатая ZIP-папка**. Выбранные файлы будут сжаты в ZIP-файл.

1. Поместите новый ZIP-файл в тот же каталог, где находится старый ZIP-файл.

1. Удалите извлеченные файлы шаблона и ZIP-файл старого шаблона.

## <a name="monitor-the-event-log"></a>Мониторинг журнала событий

Visual Studio регистрирует ошибки, обнаруживаемые при обработке ZIP-файлов шаблона. Если шаблон не отображается должным образом в диалоговом окне **Новый проект**, вы можете воспользоваться **средством просмотра событий** для устранения неполадки.

### <a name="to-locate-template-errors-in-event-viewer"></a>Поиск ошибок шаблона в средстве просмотра событий

1. В Windows в меню **Пуск** выберите **Средства администрирования Windows** > **Средство просмотра событий**.

1. В левой области выберите **Журналы Windows** > **Приложения**.

1. Найдите события, у которых `Visual Studio - VsTemplate` имеет значение **Source**.

1. Чтобы просмотреть ошибку, дважды щелкните событие шаблона.

## <a name="enable-diagnostic-logging"></a>Включение ведения журнала диагностики

Чтобы включить ведение журнала диагностики для обнаружения шаблонов, выполните действия, описанные в разделе [Устранение неполадок обнаружения шаблонов (расширяемость)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>См. также

[Устранение неполадок обнаружения шаблонов (расширяемость)](../extensibility/troubleshooting-template-discovery.md)  
[Настройка шаблонов](../ide/customizing-project-and-item-templates.md)  
[Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)  
[Справочник по схемам шаблонов](../extensibility/visual-studio-template-schema-reference.md)