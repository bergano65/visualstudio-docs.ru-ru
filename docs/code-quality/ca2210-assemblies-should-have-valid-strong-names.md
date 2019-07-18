---
title: CA2210. Сборки должны иметь допустимые строгие имена
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89edba30a95d61268aebb26de8d973f6201c0fcf
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714765"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210. Сборки должны иметь допустимые строгие имена

|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Сборка не подписана строгим именем, не удалось проверить строгое имя или строгого имени, будет недействителен без текущие параметры реестра компьютера.

## <a name="rule-description"></a>Описание правила

Это правило получает и проверяет строгое имя сборки. Нарушение возникает, если одно из следующих условий:

- Сборка имеет строгое имя.

- Сборка была изменена после подписания.

- Сборка является отложенной подписью.

- Сборка была подписана неверно или не удалось войти.

- Сборки требуются параметры реестра для проверки. Например чтобы пропустить проверку сборки использовался программы строгих имен (Sn.exe).

Строгое имя защищает клиентов от случайной загрузки сборки, которая была подменена. Сборки без строгих имен следует развертывать лишь в крайне небольшом числе случаев. При обмене или распространении сборок без правильной подписи сборки могут быть подменены, среда CLR может не загрузить сборку или пользователь может быть вынужден отключить проверку на своем компьютере. Сборку без строгого имени имеет следующие недостатки:

- Не удается проверить их истоков.

- Среда CLR не может предупредить пользователей, если содержимое сборки было изменено.

- Не удалось загрузить в глобальном кэше сборок.

Обратите внимание на то, что для загрузки и анализа сборки с отложенной подписью, необходимо отключить проверку сборки.

## <a name="how-to-fix-violations"></a>Устранение нарушений

### <a name="create-a-key-file"></a>Создать файл ключа

Используйте один из следующих процедур.

- Используйте [средство компоновщик сборок (Al.exe)](/dotnet/framework/tools/al-exe-assembly-linker).

- Для .NET Framework 2.0, используйте `/keyfile` или `/keycontainer` параметр компилятора [/keyfile (определение ключа или пары ключей для подписи сборки)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly) или  [ /keycontainer (определение контейнера ключей для подписи сборки)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) параметров компоновщика с C++).

- Для .NET Framework v1.0 и v1.1, использовать <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> или <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> атрибута.

### <a name="sign-your-assembly-with-a-strong-name-in-visual-studio"></a>Подписать сборку строгим именем в Visual Studio

1. В Visual Studio откройте решение.

2. В **обозревателе решений**, щелкните правой кнопкой мыши проект и нажмите кнопку **свойства.**

3. Нажмите кнопку **подписывание** и выберите **подписать сборку** "флажок".

4. Из **выберите файл ключа строгого имени**выберите **New**.

   **Создание ключа строгого имени** окне будут отображаться.

5. В **имя файла ключа**, введите имя для ключа строгого имени.

6. Выберите, следует ли защитить ключ паролем и нажмите кнопку **ОК**.

7. В **обозревателе решений**, щелкните правой кнопкой мыши проект и нажмите кнопку **построения**.

### <a name="sign-your-assembly-with-a-strong-name-outside-visual-studio"></a>Подписать сборку строгим именем вне Visual Studio

Используйте [средство строгих имен (Sn.exe)](/dotnet/framework/tools/sn-exe-strong-name-tool).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Только подавить предупреждение из этого правила, если сборка используется в среде, где незаконное содержимое не имеет значения.

## <a name="see-also"></a>См. также

- <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>
- <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
- [Практическое руководство. Подписание сборки строгим именем](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)
- [Sn.exe (средство строгих имен)](/dotnet/framework/tools/sn-exe-strong-name-tool)