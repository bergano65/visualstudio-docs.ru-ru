---
title: "Новые возможности Visual Studio SDK 2017 г. | Документы Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 221f4911981deec0330f76a82c0cc8a1b968e56e
ms.openlocfilehash: 60898d7cace1c10006436a8d98cbd7f7628cf972
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Новые возможности Visual Studio SDK 2017 г.

>**Примечание:** этот документ является предварительным и зависимости в выпуске версии-Кандидата Visual Studio 2017 г.

Пакет SDK для Visual Studio содержит следующие новые и обновленные средства для Visual Studio 2017 г.

## <a name="vsix-v3-format"></a>Формат v3 VSIX

Для поддержки новой установки простых Visual Studio 2017 г., формат манифеста расширения VSIX был обновлен до версии 3 (VSIX v3).

Новый формат есть поддержка:

* Явно объявив предварительные требования для выявления и установленные VSIXInstaller.
* Ngen'ing сборки на установке расширения.
* Установка средств вне корневого каталога обычные расширения.

Чтобы узнать об этих изменениях см. следующие разделы:

* [Изменения расширяемости для 2017 г.](breaking-changes-2017.md)
* [Поддержка NGen в VSIX v3](ngen-support.md)
* [Установка вне папки расширения](set-install-root.md)
* [Вопросы и ответы по расширяемости Visual Studio 2017 г.](faq-2017.md)

## <a name="migrating-extensibility-project-to-visual-studio-2017"></a>Перенос проекта расширения для Visual Studio 2017 г.

Чтобы узнать, как обновить проекты расширения среды и манифесты VSIX до 2017 г. Visual Studio, см. раздел [как: перенос проекты расширения среды для Visual Studio 2017 г](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="lightweight-solution-load-lsl"></a>Простое решение нагрузки (LSL)

Облегченная загрузить решение — это новая функция в VS 2017 г которого будет существенно снижено время загрузки решения, позволяя работать быстрее, эффективнее. При включении LSL Visual Studio не загрузится полностью проектов до начала работы с ними.

LSL может влиять на расширения Visual Studio. Расширения, которого функции зависят от проекта загружается полностью может не работать или работать неправильно. . В разделе [загрузке решения облегченного](lightweight-solution-load-extension-impact.md) ли расширение может отрицательно повлиять на и получите рекомендации по обновлению расширения.

## <a name="custom-project-and-item-templates"></a>Настраиваемые шаблоны проектов и элементов

Начиная с Visual Studio 2017 г., проверка на предмет пользовательский проект и шаблоны элементов больше не выполняется. Вместо этого расширения необходимо предоставить шаблон файлами манифеста, которые описывают расположение установки этих шаблонов. Чтобы обновить расширения VSIX можно использовать Visual Studio 2017 г. При развертывании расширения с помощью MSI, необходимо создать файлы манифеста шаблона вручную. Дополнительные сведения см. в разделе [обновление пользовательских шаблонов проектов и элементов для Visual Studio 2017 г](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Шаблон манифеста является документирована в [Visual Studio манифеста Справочник по схеме шаблонов](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Рекомендации по производительности обновленного расширения

Новая [как: диагностики производительности расширения](how-to-diagnose-extension-performance.md) подраздела [управление VSPackages](managing-vspackages.md) показано, как обнаруживать и анализировать влияние расширения для Visual Studio запуска и решение нагрузки раз.

