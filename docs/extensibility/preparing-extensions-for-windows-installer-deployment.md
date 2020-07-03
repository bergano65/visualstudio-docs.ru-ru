---
title: Подготовка расширений для развертывания установщик Windows | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74cfdcaf5b9f9babe9eefed59f1ea62478434e66
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85906156"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Подготовка расширений для развертывания установщик Windows
Нельзя использовать пакет установщик Windows (MSI) для развертывания пакета VSIX. Однако можно извлечь содержимое пакета VSIX для развертывания MSI. В этом документе показано, как подготовить проект, выходные данные которого по умолчанию — пакет VSIX для включения в проект установки.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Подготовка проекта расширения для развертывания установщик Windows
 Перед добавлением в проект установки выполните эти действия в новых проектах расширений.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Подготовка проекта расширения для развертывания установщик Windows

1. Создание пакета VSPackage, элемента MEF, оформления редактора или другого типа проекта расширяемости, включающего манифест VSIX.

2. Откройте манифест VSIX в редакторе кода.

3. Задайте `InstalledByMsi` для элемента манифеста VSIX значение `true` . Дополнительные сведения о манифесте VSIX см. в разделе [Справочник по схеме расширения vsix 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).

     Это предотвращает попытку установщика VSIX установить компонент.

4. Щелкните правой кнопкой мыши проект в **Обозреватель решений** и выберите пункт **свойства**.

5. Перейдите на вкладку **VSIX** .

6. Установите флажок **Копировать содержимое VSIX в следующее расположение** и введите путь, по которому проект установки будет выбирать файлы.

## <a name="extract-files-from-an-existing-vsix-package"></a>Извлечение файлов из существующего пакета VSIX
 Выполните следующие действия, чтобы добавить содержимое существующего пакета VSIX в проект установки, если отсутствуют исходные файлы.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>Извлечение файлов из существующего пакета VSIX

1. Переименуйте *. VSIX* файл, содержащий расширение *filename. vsix* для *filename.zip*.

2. Скопируйте содержимое *ZIP* -файла в каталог.

3. Удалите файл *[Content_types]. XML* из каталога.

4. Измените манифест VSIX, как показано в предыдущей процедуре.

5. Добавьте остальные файлы в проект установки.

## <a name="see-also"></a>Дополнительно
- [Развертывание установщика Visual Studio](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
- [Пошаговое руководство. Создание настраиваемого действия](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))
