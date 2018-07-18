---
title: Подготовка расширения для развертывания установщика Windows | Документы Microsoft
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
ms.openlocfilehash: ef51b3cb0f84a470f104ff688c1149e607d16f71
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136330"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Подготовка расширения для развертывания установщика Windows
Пакет установщика Windows (MSI) нельзя использовать для развертывания пакета VSIX. Тем не менее можно извлечь содержимое пакета VSIX для развертывания MSI. В этом документе показано, как подготовить проект, выходные данные которого по умолчанию — это пакет VSIX для включения в проект установки.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Подготовка проект расширения для развертывания установщика Windows  
 Прежде чем добавлять в проект установки, выполните следующие действия на новые проекты расширения.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Чтобы подготовить проект расширения для развертывания установщика Windows  
  
1.  Создайте пакет VSPackage, компонент MEF, оформления редактора или другого типа проекта расширяемости, который включает в себя манифест VSIX.  
  
2.  Откройте манифест VSIX Размещаются в редакторе кода.  
  
3.  Задать элемент InstalledByMsi манифеста VSIX для `true`. Дополнительные сведения о манифесте VSIX см. в разделе [Справочник по схеме 2.0 расширения VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Это предотвращает попытки установить компонент установщик VSIX.  
  
4.  Щелкните правой кнопкой мыши проект в **обозревателе решений** и нажмите кнопку **свойства**.  
  
5.  Выберите **VSIX** вкладки.  
  
6.  Установите флажок **содержимое копирования VSIX в следующее расположение** и введите путь, где будет окрашена в проект установки файлов.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>Извлечение файлов из существующего пакета VSIX  
 Выполните следующие шаги для добавления в проект установки содержимое существующего пакета VSIX, при отсутствии исходных файлов.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Чтобы извлечь файлы из существующего пакета VSIX  
  
1.  Переименовать. Файл VSIX, содержащий расширение от *filename*.vsix для *filename*.zip.  
  
2.  Скопируйте содержимое ZIP-файл в каталог.  
  
3.  Удалите файл [Content_types] .xml из каталога.  
  
4.  Измените манифест VSIX, как показано в предыдущей процедуре.  
  
5.  Добавьте оставшиеся файлы в проект установки.  
  
## <a name="see-also"></a>См. также  
 [Развертывание установщика Visual Studio](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Пошаговое руководство: Создание настраиваемого действия](http://msdn.microsoft.com/en-us/4bd4b63a-2b91-431e-839c-5752443f0eaf)