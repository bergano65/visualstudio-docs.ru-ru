---
title: Устранение неполадок, связанных с загрузкой шаблона проекта и шаблона элемента
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cc8507388e4ef9311aeb5345e5f91bd43340f5d0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027416"
---
# <a name="how-to-troubleshoot-templates"></a>Как выполнить Устранение неполадок, связанных с шаблонами

Если шаблон не загружается в среде разработки, локализовать проблему можно несколькими способами.

## <a name="validate-the-vstemplate-file"></a>Проверка файла VSTEMPLATE

Если файл *VSTEMPLATE* в шаблоне не соответствует схеме шаблона Visual Studio, шаблон может не отображаться в диалоговом окне **Новый проект**.

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