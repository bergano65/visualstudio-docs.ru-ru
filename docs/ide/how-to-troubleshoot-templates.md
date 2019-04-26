---
title: Устранение неполадок, связанных с загрузкой шаблона проекта и шаблона элемента
ms.date: 01/02/2018
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 70782646a52a5bca5741a864eee1f965941bb34b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62547597"
---
# <a name="how-to-troubleshoot-templates"></a>Как выполнить Устранение неполадок, связанных с шаблонами

Если шаблон не загружается в среде разработки, локализовать проблему можно несколькими способами.

## <a name="validate-the-vstemplate-file"></a>Проверка файла VSTEMPLATE

::: moniker range="vs-2017"

Если файл *VSTEMPLATE* в шаблоне не соответствует схеме шаблона Visual Studio, шаблон может не отображаться в диалоговом окне **Новый проект**.

::: moniker-end

::: moniker range=">=vs-2019"

Если файл *VSTEMPLATE* в шаблоне не соответствует схеме шаблона Visual Studio, шаблон может не отображаться в диалоговом окне создания проектов.

::: moniker-end

### <a name="to-validate-the-vstemplate-file"></a>Процедура проверки файла VSTEMPLATE

1. Найдите *ZIP*-файл, содержащий шаблон.

1. Извлеките содержимое *ZIP*-файла.

1. В Visual Studio в меню **Файл** выберите **Открыть** > **Файл**.

1. Выберите файл *VSTEMPLATE* для шаблона и нажмите кнопку **Открыть**.

1. Убедитесь в том, что XML-код в файле *VSTEMPLATE* соответствует схеме шаблона. Дополнительные сведения о схеме *VSTEMPLATE* см. в [справочнике по схеме шаблонов](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Чтобы обеспечить поддержку IntelliSense во время работы с файлом *VSTEMPLATE*, добавьте атрибут `xmlns` в элемент `VSTemplate` и присвойте ему значение http://schemas.microsoft.com/developer/vstemplate/2005.

1. Сохраните файл *VSTEMPLATE* и закройте его.

1. Выберите включенные в шаблон файлы, щелкните правой кнопкой мыши и выберите пункты **Отправить** > **Сжатая ZIP-папка**. Выбранные файлы будут сжаты в *ZIP*-файл.

1. Поместите новый *ZIP*-файл в тот же каталог, где находится старый *ZIP*-файл.

1. Удалите извлеченные файлы шаблона и *ZIP*-файл старого шаблона.

## <a name="enable-diagnostic-logging"></a>Включение ведения журнала диагностики

Чтобы включить ведение журнала диагностики для обнаружения шаблонов, выполните действия, описанные в разделе [Устранение неполадок обнаружения шаблонов (расширяемость)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>См. также

- [Устранение неполадок обнаружения шаблонов (расширяемость)](../extensibility/troubleshooting-template-discovery.md)
- [Настройка шаблонов](../ide/customizing-project-and-item-templates.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Справочник по схемам шаблонов](../extensibility/visual-studio-template-schema-reference.md)