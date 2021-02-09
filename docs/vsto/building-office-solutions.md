---
title: Создание решений Office
description: Изучите различия между созданием и отладкой проектов Office, а также созданием и отладкой других типов проектов в Visual Studio, таких как Windows Forms.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- debugging [Office development in Visual Studio]
- debugging Office applications in Visual Studio
- solutions [Office development in Visual Studio], debugging
- Office applications [Office development in Visual Studio], debugging
- application development [Office development in Visual Studio], building
- Office applications [Office development in Visual Studio], building
- projects [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], building
- solutions [Office development in Visual Studio], building
- Office projects [Office development in Visual Studio], debugging
- projects [Office development in Visual Studio], building
- builds [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], building
- application development [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], debugging
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 31cb28ad2c332d0afea9bef8cbe1c979b58536e6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896713"
---
# <a name="build-office-solutions"></a>Создание решений Office
  Сборка и отладка проектов Office в принципе не отличается от сборки и отладки других типов проектов в Visual Studio, например Windows Forms. В этом разделе описываются существующие различия. Общие сведения о создании приложений см. [в разделе Компиляция и сборка в Visual Studio](../ide/compiling-and-building-in-visual-studio.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="project-output-for-office-projects"></a>Выходные данные проекта для проектов Office
 Выходным каталогом проектов Office является каталог *имя_проекта*\bin\release или *имя_проекта*\bin\debug. Нельзя выполнять сборку в каталог развертывания.

### <a name="document-level-projects"></a>Проекты уровня документа
 При сборке проекта уровня документа в выходной каталог проекта включаются следующие элементы:

- копия документа проекта;

- сборка проекта и все связанные сборки, свойству **Копировать локально** которых присвоено значение **true**;

- Манифест приложения с расширением *manifest*. Дополнительные сведения см. в статье [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

- Манифест развертывания с именем файла Extension. *VSTO*. Дополнительные сведения см. в разделе [манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md).

- Файл базы данных программы (*pdb*).

> [!NOTE]
> Если сборка решения выполняется не на локальный компьютер, а в удаленное расположение, добавьте полный путь к нему в список надежных расположений в центре управления безопасностью приложения. Дополнительные сведения см. в разделе Предоставление доверия документам в [защищенных решениях Office](../vsto/securing-office-solutions.md).

### <a name="application-level-projects"></a>Проекты уровня приложения
 При построении проекта надстройки VSTO в выходные данные проекта включаются следующие элементы:

- сборка проекта и все связанные сборки, свойству **Копировать локально** которых присвоено значение **true**;

- Манифест приложения с расширением *manifest*. Дополнительные сведения см. в статье [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

- Манифест развертывания с именем файла Extension. *VSTO*. Дополнительные сведения см. в разделе [манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md).

- Файл базы данных программы (*pdb*) для сборки проекта.

  При сборке проектов надстроек VSTO на компьютере разработчика также создаются записи в реестре, необходимые для загрузки надстройки VSTO. Дополнительные сведения см. в разделе [записи реестра для надстроек VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

  При сборке проекта надстройки Outlook VSTO, содержащего области формы, в реестр добавляются следующие дополнительные данные:

- Раздел для каждого класса сообщений, связанного с одной или несколькими областями формы.

- Запись для каждой области формы и соответствующее значение, представляющее имя надстройки Outlook VSTO.

  Приложение Outlook использует эту информацию для загрузки областей форм.

## <a name="referenced-assemblies"></a>Связанные сборки
 Вы можете ссылаться на сборки (включая проекты библиотеки классов) из проекта сборки решений Office. Каждая сборка, на которую существует ссылка, имеет свойство **Копировать локально**. Свойство **Копировать локально** указывает, копируется ли сборка в выходной каталог. По умолчанию задано **значение true**. Каждая связанная сборка, свойству **Копировать локально** которой присвоено значение **true** , копируется в выходной каталог.

## <a name="security-during-the-build-process"></a>Безопасность во время процесса сборки
 Visual Studio автоматически настраивает параметры безопасности на компьютере разработчика, чтобы обеспечить предоставление решению доверия во время сборки. Это позволяет решению выполняться во время отладки.

 Проекты Office используют сертификаты для проверки издателя. Visual Studio автоматически создает временный сертификат для идентификации решений Office и настраивает на компьютере разработчика доверие к временному сертификату.

 Дополнительные сведения см. в статье [Защита решений Office](../vsto/securing-office-solutions.md).

### <a name="network-projects"></a>Сетевые проекты
 Если сборка или документ расположены в сетевой папке, обновления локальной политики безопасности (на уровне пользователя) недостаточно для запуска решения. Администратор должен предоставить полное доверие на уровне компьютера к документам и сборкам, находящимся в сетевой папке, перед запуском решения. Дополнительные сведения о настройке политики безопасности см. в статье [Защита решений Office](../vsto/securing-office-solutions.md).

 Для проектов уровня документа необходимо также добавить полный путь к расположению документа в список надежных папок Office. Дополнительные сведения см. в разделе [Предоставление доверия документам](../vsto/granting-trust-to-documents.md).

## <a name="change-the-platform-target"></a>Изменение целевой платформы
 Целевой платформой по умолчанию для проектов Office является **Любой ЦП**. Этот параметр обычно не следует изменять. Решения Office, собранные с параметром целевой платформы **Любой ЦП** , выполняются в 32- и 64-разрядных версиях Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] или [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].

 Целевую платформу x64 следует задавать, если вы создаете решение, которое будет выполняться только в 64-разрядных версиях Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] или [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]и вызывать встроенные 64 разрядные интерфейсы API. Дополнительные сведения об изменении параметра целевой платформы см. в разделе [как настроить проекты для целевых платформ](../ide/how-to-configure-projects-to-target-platforms.md).

 Если задана целевая платформа x64, решение не будет запускаться в 32-разрядных версиях Windows или Office. Если в качестве целевой платформы используется процессор x64, решение должно выполняться в 64-разрядном процессе.

## <a name="use-the-clean-command"></a>Использование команды Clean
 Для удаления файлов, созданных при сборке проекта, с компьютера разработчика можно использовать команду **Очистить** в меню **Сборка** среды [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Команда **Очистить** удаляет все файлы в каталоге выходных файлов сборки. Для проектов на уровне приложения команда **Очистить** также удаляет записи реестра, созданные в процессе сборки.

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Отладка проектов Office](../vsto/debugging-office-projects.md)|Описываются проблемы, которые могут возникать при отладке проектов Office.|
|[Пошаговое руководство. Создание первой настройки уровня документа для Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Содержит сведения о создании базовой настройки на уровне документа для Excel.|
|[Пошаговое руководство. Повторное включение надстройки VSTO, которая была отключена](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|Описание повторного включения надстройки VSTO, которая была отключена жестко или программно.|
|[Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)|Содержит ссылки на сведения о создании решений Office и о роли сборок в решении.|