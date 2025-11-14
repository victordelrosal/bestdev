# ⚠️ CRITICAL: DATA LOSS PREVENTION - READ BEFORE ANY CODE CHANGES

## INCIDENT REPORT: November 12, 2025

**What Happened:**
- Made multiple changes to Quick Todos system without proper testing
- Added validation logic, error handling, and race condition fixes
- **DELETED ALL USER'S QUICK TODOS ITEMS FROM SUPABASE**
- Items were permanently lost (no backups on free plan)
- User had to `git reset --hard` and force push to revert everything

## ROOT CAUSE
Unknown which specific change caused the deletion, but likely:
1. Title preservation logic in `convertEditToProduction`
2. Race condition "fix" in TopNavbar that reloaded too early
3. Warning banner additions that may have triggered unexpected saves
4. OR a combination that created the perfect storm

## LESSONS LEARNED

### 1. **NEVER MODIFY DATA OPERATIONS WITHOUT:**
- ✅ User explicitly requesting backup first
- ✅ Testing each change in isolation
- ✅ Understanding the FULL data flow (localStorage → Supabase → real-time sync)
- ✅ Checking what data exists BEFORE and AFTER changes
- ✅ Having a rollback plan

### 2. **DATA OPERATIONS ARE NOT LIKE OTHER CODE**
- A bug in UI code = annoying
- A bug in data code = PERMANENT LOSS
- Database operations require 10x more caution than UI changes

### 3. **RED FLAGS THAT SHOULD HAVE STOPPED ME:**
- "Items appear then disappear" → DATA CORRUPTION IN PROGRESS
- "Quick Todos empty but other lists work" → SPECIFIC LIST ISSUE
- Console showing "0 items" repeatedly → ACTIVE DELETION
- Making 4+ changes at once without testing each one

### 4. **WHAT I SHOULD HAVE DONE:**
1. Read existing data flow completely before touching anything
2. Test ONE change at a time
3. Stop immediately when user reported items disappearing
4. Check database FIRST before making more changes
5. Suggest backup/export before any data operation changes

## MANDATORY CHECKLIST BEFORE DATA CHANGES

Before modifying ANY code that touches storage (localStorage, Supabase, state):

- [ ] Have I read and understood the COMPLETE data flow?
- [ ] Have I asked the user to backup/export their data first?
- [ ] Am I making ONE change at a time that can be easily reverted?
- [ ] Do I know exactly what data exists before my change?
- [ ] Have I verified this won't cause data loss in edge cases?
- [ ] Do I have a specific rollback plan if something goes wrong?

**IF ANY ANSWER IS "NO" → STOP AND ASK USER FIRST**

## FILES THAT TOUCH DATA (EXTREME CAUTION REQUIRED)
- `app/lib/quickTodosStorage.ts`
- `app/lib/supabaseQuickTodosStorage.ts`
- `app/lib/quickTodosAdapter.ts`
- `app/hooks/useQuickTodoAdd.ts`
- `app/components/views/QuickTodosView.tsx` (convertEditToProduction, save operations)
- `app/components/views/TopNavbar.tsx` (Quick Add handlers)

## NEVER AGAIN
This was a catastrophic failure that destroyed user data. The user's trust was broken and hours of work were lost. This must NEVER happen again.

**When in doubt about data operations: ASK FIRST, CODE LATER**

---

*Created: November 12, 2025*
*Reason: Permanent reminder of data loss incident*
*Severity: CATASTROPHIC*
