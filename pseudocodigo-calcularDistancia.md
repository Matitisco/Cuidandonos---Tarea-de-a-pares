

Viaje >> public static double calcularTiempoDeDemoraPromedio(calculadorTiempoDemora: CalculadorTiempoDemora, velocidadPromedio: Double) { 
        double tiempoTotal = 0.0;

   

        for (paradas) {
            
            tiempoTotalDemora += calculadorTiempoDemora.calcularTiempoDemora(adapterCalcularDistancia);
        }

        return tiempoTotalDemora / listaViajes.size();



}



calculadorTiempoDemora >> public double calcularTiempoDemora(AdapterCalcularDistancia adapter, velocidadPromedio: Double) {
        double tiempoDemora = 0.0;
        

        tiempoDemora = adapter.calcularDistancia() / velocidadPromedio;

        return tiempoDemora;
}