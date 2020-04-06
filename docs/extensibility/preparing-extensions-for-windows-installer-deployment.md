---
title: Подготовка расширений для развертывания установки Windows (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8636dfbbad06192e5edbb61a9a784f64b8f3f14f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702030"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Подготовка расширений для развертывания установки Windows
Для развертывания пакета VSIX нельзя использовать пакет установки Windows (MSI). Тем не менее, можно извлечь содержимое пакета VSIX для развертывания MSI. В этом документе показано, как подготовить проект, выход по умолчанию которого является пакетом VSIX для включения в проект настройки.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Подготовьте проект расширения для развертывания установки Windows
 Выполните эти шаги по новым проектам расширения, прежде чем добавить в проект настройки.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Подготовить проект расширения для развертывания установки Windows

1. Создайте компонент VSPackage, MEF, украшение редактора или другой тип проекта расширения, который включает манифест VSIX.

2. Откройте манифест VSIX в редакторе кода.

3. Установите `InstalledByMsi` элемент манифеста VSIX. `true` Для получения дополнительной информации о [VSIX extension schema 2.0 reference](../extensibility/vsix-extension-schema-2-0-reference.md)манифесте VSIX см.

     Это предотвращает попытку установки компонента установщиком VSIX.

4. Нажмите правой кнопкой мыши проекта в **Solution Explorer** и нажмите **Свойства**.

5. Выберите вкладку **VSIX.**

6. Проверьте поле с маркировкой **содержимого Copy VSIX** на следующем месте и введите путь, по которому проект настройки будет забрать файлы.

## <a name="extract-files-from-an-existing-vsix-package"></a>Извлечение файлов из существующего пакета VSIX
 Выполните эти действия, чтобы добавить содержимое существующего пакета VSIX в проект настройки, если у вас нет исходных файлов.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>Извлечение файлов из существующего пакета VSIX

1. Переименуй *. Файл VSIX,* содержащий расширение с *filename.vsix* на *filename.zip*.

2. Копируйте содержимое файла *.zip* в каталог.

3. Удалите файл *«Content_types.xml* из каталога.

4. Оторите манифест VSIX, как показано в предыдущей процедуре.

5. Добавьте оставшиеся файлы в проект настройки.

## <a name="see-also"></a>См. также
- [Развертывание установки Visual Studio](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
- [Прохождение: Создание пользовательского действия](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))
