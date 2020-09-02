---
title: Подготовка расширений для развертывания установщик Windows | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 76d7f879fade99914bf3f56ade0ec1270e14f4c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694591"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Подготовка расширений для развертывания с помощью установщика Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Нельзя использовать пакет установщик Windows (MSI) для развертывания пакета VSIX. Однако можно извлечь содержимое пакета VSIX для развертывания MSI. В этом документе показано, как подготовить проект, выходные данные которого по умолчанию — пакет VSIX для включения в проект установки.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Подготовка проекта расширения к развертыванию установщик Windows  
 Перед добавлением в проект установки выполните эти действия в новых проектах расширений.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Подготовка проекта расширения для развертывания установщик Windows  
  
1. Создание пакета VSPackage, элемента MEF, оформления редактора или другого типа проекта расширяемости, включающего манифест VSIX.  
  
2. Откройте манифест VSIX в редакторе кода.  
  
3. Установите для элемента InstalledByMsi манифеста VSIX значение `true` . Дополнительные сведения о манифесте VSIX см. в разделе [Справочник по схеме расширения vsix 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Это предотвращает попытку установщика VSIX установить компонент.  
  
4. Щелкните правой кнопкой мыши проект в **Обозреватель решений** и выберите пункт **свойства**.  
  
5. Перейдите на вкладку **VSIX** .  
  
6. Установите флажок **Копировать содержимое VSIX в следующее расположение** и введите путь, по которому проект установки будет выбирать файлы.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>Извлечение файлов из существующего пакета VSIX  
 Выполните следующие действия, чтобы добавить содержимое существующего пакета VSIX в проект установки, если отсутствуют исходные файлы.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Извлечение файлов из существующего пакета VSIX  
  
1. Переименуйте. VSIX-файл, содержащий расширение *filename*. VSIX в *filename*. zip.  
  
2. Скопируйте содержимое ZIP-файла в каталог.  
  
3. Удалите файл [Content_types]. XML из каталога.  
  
4. Измените манифест VSIX, как показано в предыдущей процедуре.  
  
5. Добавьте остальные файлы в проект установки.  
  
## <a name="see-also"></a>См. также:  
 [Развертывание Visual Studio Installer](https://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Пошаговое руководство. Создание настраиваемого действия](https://msdn.microsoft.com/4bd4b63a-2b91-431e-839c-5752443f0eaf)
