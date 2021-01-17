---
title: Calculators
layout: default
excerpt: "Calculators for easier simulations"
---

<style>
    .calc_container {
        display: flex;
        text-align: center;
        margin: auto;
        width: 50%;
        padding: 10px;
    }

    .Y_Est {
        display: inline-block;
        margin-left: auto;
        margin-right: auto;
        text-align: left;
        border-radius: 15px 50px;
        border-color: blue;
        border-style: solid;
        background: black;
        font-weight: bold;
        color: white;
    }

    td {
        padding-right: 20px;
        padding-left: 20px;
    }

    .button1 {
        display:inline-block;
        margin:0 0.3em 0.3em 0;
        -ms-transform: translateX(70%);
        transform: translateX(70%);
    }
}


</style>

<script>
    <!-- 
    function y_plus_estimation(form) {

        u_freestream = eval(form.u_freestream.value)
        if (u_freestream <= 0.0) {
            alert("Free stream velocity must be greater than zero")
            return
        }

        rho = eval(form.rho.value)
        if (rho <= 0.0) {
            alert("Density must be greater than zero")
            return
        }

        L = eval(form.L.value)
        if (L <= 0.0) {
            alert("Boundary layer reference length must be greater than zero")
            return
        }

        mu = eval(form.mu.value)
        if (mu <= 0.0) {
            alert("Dynamic viscosity must be greater than zero")
            return
        }

        y_plus_desired = eval(form.y_plus_desired.value)
        if (y_plus_desired <= 0.0) {
            alert("Desired y+ value must be greater than zero")
            return
        }

        Re = (rho * u_freestream/100 * L/1000) / mu
        C_f = 0.026 * Math.pow(Re, -(1.0 / 7.0))
        C_f = 0.0576 * Math.pow(Re, -1.0 / 5.0)
        C_f = 0.370 * Math.pow(Math.log(Re) / Math.log(10), -2.584)
        C_f = Math.pow((2 * Math.log(Re) / Math.log(10) - 0.65), -2.3)
        tau_w = C_f * 0.5 * rho * u_freestream * u_freestream
        U_f = Math.sqrt(tau_w / rho)

        wall_distance_estimation = 1000*(y_plus_desired * mu) / (U_f * rho)

        form.Re.value = Re.toFixed(3)
        form.wall_distance_estimation.value = wall_distance_estimation.toFixed(10)
    }

    // end hide 
    -->
</script>


{% include site-header.html %}


<div class="calc_container">
  <form class="Y_Est">
    <table cellspacing="10">
      <tbody>
        <tr>
          <td colspan="3"><b>
              <center>First Layer Height Estimation</center>
            </b>
            <hr>
          </td>
        </tr>
        <tr></tr>
      </tbody>
      <tbody>
        <tr>
          <td colspan="3"><b>Input</b>
            <hr>
          </td>
        </tr>
        <tr>
          <td>Freestream velocity:</td>
          <td><input type="text" id="u_freestream" name="u_freestream" value="50.0" size="16"></td>
          <td>[cm/s]</td>
        </tr>
        <tr>
          <td>Density:</td>
          <td><input type="text" id="rho" name="rho" value="1060" size="16"></td>
          <td>[kg/m<sup>3</sup>]</td>
        </tr>
        <tr>
          <td>Dynamic viscosity:</td>
          <td><input type="text" id="mu" name="mu" value="3.3e-3" size="16"></td>
          <td>[kg/m-s]</td>
        </tr>
        <tr>
          <td>Boundary Layer Length:</td>
          <td><input type="text" id="L" name="L" value="10.0" size="16"></td>
          <td>[mm]</td>
        </tr>
        <tr>
          <td>Desired Y+ value:</td>
          <td><input type="text" id="y_plus_desired" name="y_plus_desired" value="1.0" size="16"></td>
          <td></td>
        </tr>
        <tr>
          <td colspan="3"><br></td>
        </tr>
        <tr>
          <td colspan="3"><b>Output</b>
            <hr>
          </td>
        </tr>
        <tr>
          <td>Reynolds number:</td>
          <td><input type="text" id="Re" name="Re" size="16"></td>
          <td></td>
        </tr>
        <tr>
          <td>Estimated wall distance:</td>
          <td><input type="text" id="wall_distance_estimation" name="wall_distance_estimation" size="16"></td>
          <td>[mm]</td>
        </tr>
        <tr>
          <td colspan="3">&nbsp;</td>
        </tr>
        <tr>
          <td colspan="3" align="right" class="button1"><input type="button" value="Estimate Wall Distance" onclick="y_plus_estimation(this.form)"></td>
        </tr>
      </tbody>
    </table>
  </form>
</div>


{% include site-footer.html %}