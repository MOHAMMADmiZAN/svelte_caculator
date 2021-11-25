<script>

    import Key from "../Component/Key.svelte";

    let value_array = []

    function add_cal_key(e) {
        value_array = [...value_array, e.detail]
        value_array = value_array.join('')

    }

    function ce(e) {
        try {
            if (e.detail === 'CE') {
                value_array = ''

            }
        } catch (err) {
            console.log(err)
        }
    }

    function x(e) {
        try {
            if (e.detail === 'X') {
                value_array = value_array.slice(0, -1)
            }
        } catch (err) {
            console.log(err)
        }
    }

    // when eval function is dangerous //
    // alternative function of eval () reference https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/eval
    function devil(val) {
        return new Function('"use strict";return ' + val)();
    }

    function equal(e) {
        try {
            if (e.detail === '=') {
                value_array = devil(value_array)
                value_array = value_array.toString()
            }


        } catch (err) {
            console.dir(err)
        }
    }


</script>

<div class="container mt-5">
    <div class="row">
        <div class="col-lg-6 m-auto">
            <div class="card text-center">
                <div class="card-header"><h4>Svelte Calculator</h4></div>
                <div class="card-body px-0">
                    <div class="form-group">
                        <label for="cal"></label>
                        <input id="cal" type="text" class="form-control" bind:value={value_array} readonly>
                    </div>
                    <div class="key_section">
                        <Key key_value="1" on:cal_value={add_cal_key}/>
                        <Key key_value="2" on:cal_value={add_cal_key}/>
                        <Key key_value="3" on:cal_value={add_cal_key}/>
                        <Key key_value="4" on:cal_value={add_cal_key}/>
                        <Key key_value="5" on:cal_value={add_cal_key}/>
                        <Key key_value="6" on:cal_value={add_cal_key}/>
                        <Key key_value="7" on:cal_value={add_cal_key}/>
                        <Key key_value="8" on:cal_value={add_cal_key}/>
                        <Key key_value="9" on:cal_value={add_cal_key}/>
                        <Key key_value="0" on:cal_value={add_cal_key}/>
                        <Key key_value="00" on:cal_value={add_cal_key}/>
                        <Key key_value="." on:cal_value={add_cal_key}/>
                        <Key key_value="+" on:cal_value={add_cal_key}/>
                        <Key key_value="-" on:cal_value={add_cal_key}/>
                        <Key key_value="*" on:cal_value={add_cal_key}/>
                        <Key key_value="/" on:cal_value={add_cal_key}/>
                        <Key key_value="CE" on:cal_value={ce}/>
                        <Key key_value="X" on:cal_value={x}/>
                        <Key key_value="=" on:cal_value={equal} w="130px"/>
                    </div>

                </div>
            </div>
        </div>
    </div>
</div>


<style>
    .key_section {
        display: flex;
        flex-wrap: wrap;
        width: 47%;
        margin: auto;
    }

    input {
        border: 0;
        padding: 20px;
        background: #666666;
        font-weight: 900;
        font-size: 25px;

    }
</style>