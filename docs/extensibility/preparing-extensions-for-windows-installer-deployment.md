---
title: Подготовка расширений для развертывания установщика Windows | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cc742fecbbe03ff3d3aa0fb3f8d61a9c5f09254b
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495275"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Подготовка расширения для развертывания установщика Windows
Пакет установщика Windows (MSI) нельзя использовать для развертывания пакета VSIX. Тем не менее можно извлечь содержимое пакета VSIX для развертывания MSI. В этом документе показано, как подготовка проекта, выходные данные которого по умолчанию — это пакет VSIX для включения в проект установки.  
  
## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Подготовить проект расширения для развертывания установщика Windows  
 Прежде чем добавлять в проект установки, выполните следующие действия на новых проектов расширения.  
  
### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Чтобы подготовить проект расширения для развертывания установщика Windows  
  
1.  Создайте VSPackage, компонент MEF, оформления редактора или другого типа проекта расширения, включающий в манифесте VSIX.  
  
2.  Откройте манифест VSIX в редакторе кода.  
  
3.  Задайте `InstalledByMsi` манифеста VSIX для `true`. Дополнительные сведения о манифесте VSIX, см. в разделе [Справочник по схеме 2.0 расширения VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Это предотвращает попытки установки компонента установщик VSIX.  
  
4.  Щелкните правой кнопкой мыши проект в **обозревателе решений** и нажмите кнопку **свойства**.  
  
5.  Выберите **VSIX** вкладки.  
  
6.  Установите флажок **VSIX копирования содержимого в следующее расположение** и введите путь к которой проект установки скопирует файлы.  
  
## <a name="extract-files-from-an-existing-vsix-package"></a>Извлеките файлы из существующего пакета VSIX  
 Выполните следующие шаги для добавления содержимого существующего пакета VSIX в проект установки, если у вас нет исходных файлов.  
  
### <a name="to-extract-files-from-an-existing-vsix-package"></a>Чтобы извлечь файлы из существующего пакета VSIX  
  
1.  Переименовать *. VSIX* файл, содержащий расширение из *filename.vsix* для *filename.zip*.  
  
2.  Скопируйте содержимое *ZIP-файл* файл в каталог.  
  
3.  Удалить *[Content_types] .xml* файл из каталога.  
  
4.  Измените манифест VSIX, как показано в предыдущей процедуре.  
  
5.  Добавьте оставшиеся файлы проекта установки.  
  
## <a name="see-also"></a>См. также  
 [Развертывание установщика Visual Studio](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Пошаговое руководство: Создание настраиваемого действия](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))