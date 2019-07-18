---
title: Подготовка расширений для развертывания установщика Windows | Документация Майкрософт
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694591"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Подготовка расширений для развертывания с помощью установщика Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пакет установщика Windows (MSI) нельзя использовать для развертывания пакета VSIX. Тем не менее можно извлечь содержимое пакета VSIX для развертывания MSI. В этом документе показано, как подготовка проекта, выходные данные которого по умолчанию — это пакет VSIX для включения в проект установки.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Подготовка проект расширения для развертывания установщика Windows  
 Прежде чем добавлять в проект установки, выполните следующие действия на новых проектов расширения.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Чтобы подготовить проект расширения для развертывания установщика Windows  
  
1. Создайте VSPackage, компонент MEF, оформления редактора или другого типа проекта расширения, включающий в манифесте VSIX.  
  
2. Откройте манифест VSIX в редакторе кода.  
  
3. Задать элемент InstalledByMsi манифеста VSIX для `true`. Дополнительные сведения о манифесте VSIX, см. в разделе [Справочник по схеме 2.0 расширения VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Это предотвращает попытки установки компонента установщик VSIX.  
  
4. Щелкните правой кнопкой мыши проект в **обозревателе решений** и нажмите кнопку **свойства**.  
  
5. Выберите **VSIX** вкладки.  
  
6. Установите флажок **VSIX копирования содержимого в следующее расположение** и введите путь к которой проект установки скопирует файлы.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>Извлечение файлов из существующего пакета VSIX  
 Выполните следующие шаги для добавления содержимого существующего пакета VSIX в проект установки, если у вас нет исходных файлов.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Чтобы извлечь файлы из существующего пакета VSIX  
  
1. Переименовать. VSIX-файл, содержащий расширение из *filename*.vsix для *filename*ZIP-файл.  
  
2. Скопируйте содержимое ZIP-файла в каталог.  
  
3. Удалите файл [Content_types] .xml из каталога.  
  
4. Измените манифест VSIX, как показано в предыдущей процедуре.  
  
5. Добавьте оставшиеся файлы проекта установки.  
  
## <a name="see-also"></a>См. также  
 [Развертывание с помощью установщика Visual Studio](https://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Пошаговое руководство: Создание настраиваемых действий](https://msdn.microsoft.com/4bd4b63a-2b91-431e-839c-5752443f0eaf)
