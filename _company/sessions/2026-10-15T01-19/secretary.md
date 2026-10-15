# 📱 영숙 — 회사 목표, 모든 에이전트의 개인 목표, 지난 24시간 메모리를 종합적으로 요약하고, 현재 진행 중인 작업 목록과 그 상태를 브리핑합니다.

<run_command>
# 📱 영숙 에이전트에게 필요한 정보 수집 요청

# 1. 회사 및 에이전트 목표 확인 (Goal Retrieval)
# CEO 지시 및 자율 사이클 실행을 위해, 현재 회사의 최고 목표와 각 에이전트의 세부 목표가 필요합니다.
echo "Fetching Company Goal..."
cat _company/company_goal.md

echo "Fetching Agent Goals..."
# 모든 에이전트의 목표 파일 목록을 순회하며 내용을 가져옵니다.
find _agents/ -name "goal.md" -print -exec cat {} \;

# 2. 현재 진행 중인 작업 목록 및 상태 확인 (Task Status Retrieval)
# 현재 진행 중인 모든 작업(Task)과 해당 작업의 상태(Status)가 필요합니다.
echo "Fetching Current Task List and Status..."
cat _tasks/task_list.md
</run_command>

---
## 🛠️ 도구 실행 결과 (시스템 자동 실행)

### 🔧 실행: `# 📱 영숙 에이전트에게 필요한 정보 수집 요청

# 1. 회사 및 에이전트 목표 확인 (Goal Retrieval)
# CEO 지시 및 자율 사이클 실행을 위해, 현재 회사의 `
```
'#'��(��) ���� �Ǵ� �ܺ� ����, ������ �� �ִ� ���α׷�, �Ǵ�
��ġ ������ �ƴմϴ�.
```
_❌ exit 1_
