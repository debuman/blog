---
title: "윈도우11 26H2 마우스 우클릭 메뉴를 윈도우10 스타일로 변경하기"
date: 2026-11-20
deck: "Windows 10 방식의 우클릭 메뉴를 적용하거나 Windows 11 기본 메뉴로 되돌리는 방법."
tags: ["windows-11", "file-explorer", "registry"]
draft: false
---

[Read in English](/writing/2026/windows-11-classic-context-menu/)

Windows 11 26H2 업데이트 후 파일을 우클릭하면 새 메뉴가 뜬다. 예전처럼 한 번에 전체 메뉴를 열려면 다음 두 방법 중 하나를 선택한다.

## 파일로 적용하기

1. [클래식 메뉴 적용 파일 다운로드 (.reg)](/uploads/windows-11-context-menu/Enable-Classic-Menu.reg)
2. 받은 파일을 더블클릭하고 레지스트리 편집기에서 **예**를 누른다.
3. **Ctrl+Shift+Esc**로 작업 관리자를 연다. **Windows 탐색기**를 우클릭하고 **다시 시작**을 선택한다.

**기본 메뉴로 복원하려면** [복원 파일 (.reg)](/uploads/windows-11-context-menu/Restore-Windows-11-Menu.reg)을 받아 같은 순서로 적용한다.

## 레지스트리 편집기로 직접 설정하기

1. **Win+R**을 누르고 `regedit`을 실행한다. 주소 표시줄에 `HKEY_CURRENT_USER\Software\Classes\CLSID`를 붙여 넣고 **Enter**를 누른다.
2. `CLSID` 아래에 다음 두 키를 만든다(**우클릭 → 새로 만들기 → 키**). 이미 있는 키는 먼저 **내보내기**로 백업한다.
   - `{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}`
   - `{51668040-5e31-4023-bbe3-149163bd80f1}`
3. 두 키 각각에서 `InprocServer32` 하위 키를 열거나 새로 만든다. 오른쪽의 **(기본값)**을 더블클릭하고 **값 데이터**를 비운 채 **확인**을 눌러 빈 문자열을 저장한다.
4. 작업 관리자에서 **Windows 탐색기 → 다시 시작**을 선택한다.

**수동으로 복원하려면** 위의 중괄호로 된 두 키만 삭제한다. 백업해 둔 키가 있다면 해당 백업을 다시 가져온 뒤 Windows 탐색기를 다시 시작한다.
