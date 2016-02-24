code for reproducing a variable inheritance inconsistency

usage: `ansible-cookbook -i host_inventory_file site.yml`

results:

    PLAY [reproduce] **************************************************************

    GATHERING FACTS ***************************************************************
    ok: [example.com]

    TASK: [child | debug msg="before include_vars => {{ test_marker }}"] **********
    ok: [example.com] => {
        "msg": "before include_vars => child"
    }

    TASK: [child | include vars] **************************************************
    ok: [example.com]

    TASK: [child | debug msg="after include_vars => {{ test_marker }}"] ***********
    ok: [example.com] => {
        "msg": "after include_vars => child"
    }

    TASK: [child | debug msg="inside tasks.yml => {{ test_marker }}"] *************
    ok: [example.com] => {
        "msg": "inside tasks.yml => parent"
    }

    TASK: [child | debug msg="after include tasks.yml => {{ test_marker }}"] ******
    ok: [example.com] => {
        "msg": "after include tasks.yml => parent"
    }

    PLAY RECAP ********************************************************************
    example.com            : ok=6    changed=0    unreachable=0    failed=0

