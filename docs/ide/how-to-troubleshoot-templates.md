---
title: Устранение неполадок, связанных с загрузкой шаблона проекта и шаблона элемента Visual Studio | Документы Майкрософт
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: f7e952f8eb445787a2a574ae3431ba6ad8728248
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-troubleshoot-templates"></a>Практическое руководство. Устранение неполадок, связанных с шаблонами

Если шаблон не загружается в среде разработки, локализовать проблему можно несколькими способами.

## <a name="validate-the-vstemplate-file"></a>Проверка файла VSTEMPLATE

Если файл *VSTEMPLATE* в шаблоне не соответствует схеме шаблона Visual Studio, шаблон может не отображаться в диалоговом окне **Новый проект**.

### <a name="to-validate-the-vstemplate-file"></a>Процедура проверки файла VSTEMPLATE

1. Найдите *ZIP*-файл, содержащий шаблон.

1. Извлеките содержимое *ZIP*-файла.

1. В Visual Studio в меню **Файл** выберите **Открыть** > **Файл**.

1. Выберите файл *VSTEMPLATE* для шаблона и нажмите кнопку **Открыть**.

1. Убедитесь в том, что XML-код в файле *VSTEMPLATE* соответствует схеме шаблона. Дополнительные сведения о схеме *VSTEMPLATE* см. в разделе [Справочник по схеме шаблонов](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Чтобы обеспечить поддержку IntelliSense во время работы с файлом *VSTEMPLATE*, добавьте атрибут `xmlns` в элемент `VSTemplate` и присвойте ему значение http://schemas.microsoft.com/developer/vstemplate/2005.

1. Сохраните *VSTEMPLATE*-файл и закройте его.

1. Выберите включенные в шаблон файлы, щелкните правой кнопкой мыши и выберите пункты **Отправить** > **Сжатая ZIP-папка**. Выбранные файлы будут сжаты в *ZIP*-файл.

1. Поместите новый *ZIP*-файл в тот же каталог, где находится старый *ZIP*-файл.

1. Удалите извлеченные файлы шаблона и *ZIP*-файл старого шаблона.

## <a name="enable-diagnostic-logging"></a>Включение ведения журнала диагностики

Чтобы включить ведение журнала диагностики для обнаружения шаблонов, выполните действия, описанные в разделе [Устранение неполадок обнаружения шаблонов (расширяемость)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>См. также

[Устранение неполадок обнаружения шаблонов (расширяемость)](../extensibility/troubleshooting-template-discovery.md)  
[Настройка шаблонов](../ide/customizing-project-and-item-templates.md)  
[Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)  
[Справочник по схемам шаблонов](../extensibility/visual-studio-template-schema-reference.md)